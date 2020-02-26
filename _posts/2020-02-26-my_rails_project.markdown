---
layout: post
title:      "My Rails Project "
date:       2020-02-26 17:32:24 -0500
permalink:  my_rails_project
---

## Airlines 

This rails project was a doozy, it was tough but I had a lot of fun building it step by step. First step I took was to brainstorm on how the relationships will be established. Second, was to add the tables in and give them the appropriate attributes. Third, create the routes and make them work accordingly. Last, to give it a nice design for user's eyes. 
All of these steps I took made this project feel like a smooth drive to Houston.


### Brainstorming 

The very first step I took was to brainstorm the relationships between five `models` (`User, Ticket, Airline, Flight, and Passenger`)  in my application. In order from me to come up with a best relationships to hook these `models` up I had to thing of a real life situation at an airport and talk to people. What is the first thing a person most do to registure for a flight ticket? They most go online pick a airport (`Airline`) that `has_many` `flights` to `buy` a `ticket` that `belongs_to` a `flight` and `belongs_to` a `passenger` of their chose. All this can be done after the person creates a `User` account and gives it a passenger or makes the user have many `:passengers`.  How does the `Airline` know which flight each passenger is in? The Airline `has_many :passengers, through: :flights`. What about `Flights`? Flight `has_many :passengers, through: :tickets`. And how does the `Passenger` now which `flights` they are on? Passenger `has_many "flights, through: :tickets`.  Anymore more questions? 

![](https://media3.giphy.com/media/jzpLjAx4pAsP6/giphy.webp?cid=790b761107033219cd7dd36ed0b493c51f5fb8d4d8edc057&rid=giphy.webp) 

![](https://media0.giphy.com/media/ac7MA7r5IMYda/200.webp?cid=790b76117da9a31f58a01a2f49e0f336822713dd0b7dd0c5&rid=200.webp)

😆😆 All jokes aside, that was how I developed the relationships between the `models`. 


### Add Attributes
Alright, we all know a `User` account has a `username` and  `password`


