---
layout: post
title:      "What Blackjack Taught Me About AJAX"
date:       2020-06-12 02:15:48 +0000
permalink:  what_blackjack_taught_me_about_ajax
---



After creating my first javascript project with AJAX, a human vs. computer blackjack game with statistics, I want to reflect on one of my most interesting error messages and what it taught me.

#<ActiveRecord::StatementInvalid: SQLite3::BusyException: database is locked>

A quick google search clarified that SQLLite3 was not designed for concurrent database acess. This can be solved by accessing the database one request at a time. I was confused becuase I thought I was only accessing my database one request at a time using asynchronous javascript. What was causing this? 

When a user clicks "New Game" I instantiate two player objects and create a new statistics object for each player to represent this game's win/loss count for each player. 

This means I need to send a fetch request to "/players/:id" to see if the player exists, then I need to either send a fetch request to create that player OR send a fetch request for the next player. 
After that, we need to send a fetch request to create a new row in the Statistics table for each player.


The first time I encountered this error I was fetching each player without validation, then posting a fetch request to create a new row in the Statistics table.


My code looked something like this:
Note: in this context "this" is the game object. human and computer are instances of the Player class.
```
 this.human.fetchPlayer().then((resp) => {
       this.human.stats.newGameCreateStats(this.human)           
        })      
				
this.computer.fetchPlayer().then((resp) => {
       this.computer.stats.newGameCreateStats(this.computer)           
        })  
				
```

I still didn't realize my mistake right away. Eventually I noticed in the console that sometimes player 1 would be created fine, but the fetch request for player 2 would always show code 500 internal server error in the js console. I also realized that the timeout messages for player 1 and 2 were hitting at the same time in the console, not 5 seconds apart. Only then did I realize I needed to chain these to chain these together. 

This cuts to the core of what AJAX is and how code is evaluated at runtime. At runtime the first fetch request returns a Promise then runtime environment moves on to evaluate the next fetch request. This is why they both timed out at essentially the same time.

To clear the error message the code looked something like this:
```
 this.human.fetchPlayer().then((resp) => {
       this.human.stats.newGameCreateStats(this.human)           
 }).then(() => {
			 this.computer.fetchPlayer()
 }).then((resp) => {
        this.computer.stats.newGameCreateStats(this.computer)   
				return resp
})
```

The difference is that in this block of code we call the ".then()" function so that we don't try to fetch the computer player until after line 2 is resolved.

The original error message taught me more than the limitations of SQLite3, it taught me about how code is evaluated when you are using asynchronous javascript and xml (AJAX). 
It is important to pay attention to what is, and what is not chained together with the ".then()" function because that will change how code is evaluated. 


The final code checks if a player exists in the database, then creates a player if none exists. This conditional logic inside of asynchronous function calls feels like ugy, messy code to me, but it exemplifies how AJAX can be used.

The final code below sends a fetch request to "/players/:id" to see if the player exists, then either sends a fetch request to create that player OR sends a fetch request for the next player. 
After that, it sends a fetch request to "/statistics" to create a new row in the Statistics table associated with each player.
Also, notice that the last 3 lines are outside of the asynchronous block. Those three lines do not wait for the promises to resolve. 

```
this.human.fetchPlayer().then((resp) => {
            if (resp === null) {
                return this.human.fetchCreatePlayer()
            } else {
                return this.computer.fetchPlayer()
            }            
        })       
        .then((resp) => {
            if (resp === null) {
                return this.computer.fetchCreatePlayer().then((resp) => this.human.stats.newGameCreateStats(this.human))
            } else {
                return this.human.stats.newGameCreateStats(this.human)
            }            
        }).then((resp) => {
            this.human.stats.id = resp.id 
            return this.computer.stats.newGameCreateStats(this.computer)
        }).then((resp) => this.computer.stats.id = resp.id)
        
        this.gameWindow = this.displayGameWindow()

        this.buildTable()
        this.phaseOneHuman() 
```

The final code additionally takes the response from the rails API create statistic action and saves the statistic id to the javascript object "this.{player}.stats". We need that id later when we want to update the stats with the game's results. 

I really found this project fun and challenging. I am proud of the results and I look forward to continuing to build on my programming knowledge. 





