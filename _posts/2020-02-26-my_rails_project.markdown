---
layout: post
title:      "My Rails Project "
date:       2020-02-26 17:32:24 -0500
permalink:  my_rails_project
---

## Airlines 

This rails project was a doozy, it was tough but I had a lot of fun building it step by step. The first step I took was to brainstorm on how the relationships will be established. Second, was to add the tables in and give them the appropriate attributes. Third, create the routes and make them work accordingly. Last, to give it a nice design for the user's eyes and make the app have `validations`. All of these steps I took made this project feel like a smooth drive to Houston.

Using the Ruby on Rails, fortunately, comes with `ActiveRecord`, but there's still some gems I needed to add. Those gems were `Bcrypt`, `omniauth`, and`optimist`. Bcrypt was for the User account to gain more security. The gem `omniauth` followed by its inheritors `omniauth-facebook` and `omniauth-google-oauth2`  for logging into Facebook or Gmail, because these are the most ubiquitous sites used. `optimist` simply for the faced that `webpacker` is not working well for the server.  Each of these gems requires a setup after they have been installed, the requirements won't be discussed in this blog for time purposes. 
 

### Brainstorming 

The very first step I took was to brainstorm the relationships between five `models` (`User, Ticket, Airline, Flight, and Passenger`)  in my application. For me to come up with the best relationships to hook these `models` up, I had to think of a real-life situation at an airport and talk to people. What is the first thing a person must do to register for a flight ticket? They most go online pick an airport (`Airline`) that `has_many` `flights` to `buy` a `ticket` that `belongs_to` a `flight` and `belongs_to` a `passenger` of their choosing. All this can be done after the person creates a `User` account and gives it a passenger or makes the user have many `:passengers`.  How does the `Airline` know which flight each passenger is in? The Airline `has_many :passengers, through: :flights`. What about `Flights`? Flight `has_many :passengers, through: :tickets`. And how does the `Passenger` now which `flights` they are on? Passenger `has_many "flights, through: :tickets`.  Anymore more questions? 

![](https://media3.giphy.com/media/jzpLjAx4pAsP6/giphy.webp?cid=790b761107033219cd7dd36ed0b493c51f5fb8d4d8edc057&rid=giphy.webp) 

![](https://media0.giphy.com/media/ac7MA7r5IMYda/200.webp?cid=790b76117da9a31f58a01a2f49e0f336822713dd0b7dd0c5&rid=200.webp)

 All jokes aside, that was how I developed the relationships between the `models`. 


### Add Attributes

Alright, now that the models  have associated with each other properly the next step I took was adding the attributes. We all know a `User` account has a `username`, `password` most of the time, an `email`, so those will be the attributes. How do we set them up? In the `data control` (db) inside a `migrate` folder there you create a number file like so, `001_create_users.rb` and inside it you should have:

 ``` 
class CreateUsers < ActiveRecord::Migration[6.0]
   def change
    create_table :users do |t|
      t.string :username
      t.string :password_digest

      t.timestamps
    end
   end
end
```

The same goes for the other models Passenger, Ticket, Flight, and Airline. In `SQL` some of these models have a `Foreign key` you must also include as one of the attributes. Models that `belongs_to` another are the ones with this special key. Ticket belongs to both passenger and flight, so it will have two foreign keys `flight_id` and `passenger_id`.

### Create Routes

After setting up the attributes and migrating them to the database, the third step I chose was to create the routes. There are two ways so create routes, you can use the built-in rails `resources` inside the `routes.rb` located in the config folder. Or you can build your route like so:  
```
Rails.application.routes.draw do
# rails built-in 
 resources :user, only: [:login, :loggedin, :new, :create, :destroy]

 # Custom users
  get '/login', to: 'users#login'
  post '/login', to: 'users#loggedin'
  get '/signup', to: 'users#new'
  post '/signup', to: 'users#create'
  get '/logout', to: 'users#destroy'
end
```
 
Sometimes you may need to use both, in my case I did and I also had to make `nested routes` work hand and hand with models that are associated with each other. With each route created pointed `to:` `an#action` it's essential that the controller must have matching `action method` names the same goes for the views. 

### Validations and Design 

Ok now that I have got every previous task setup, the last step was to add restrictions and design. The `User` Model was the first place to add validations. The attribute username must be `validated` with `uniqueness` that way there're no accounts with the same username. Password needs  `validates` for the minimum to maximum characters it can have. 
For the other models' `validates` all their attributes must be `presence` except for one, the `Passenger` and it's set to `optional`.  Now designing comes into the app, `CSS` and rearranging content to make it look nice for the user, then the project concluded. Overall, this an experience, I enjoyed it and I learn numerous amounts of tricks. 
 
 

