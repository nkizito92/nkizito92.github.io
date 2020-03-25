---
layout: post
title:      "My SimoneSays Project"
date:       2020-03-23 20:40:26 -0400
permalink:  my_simonesays_project
---


Let just start by saying this project was pretty fun, all the step I have taken worked pretty well. Taking one step at a time is the best way to approach it. First, create the backend and generate the necessary `rails` class. Second, create the frontEnd, this contains  `HTML`, `CSS`, and `javaScript` files. Last, in the javaScript files make all the necessary `iterations`.


## Building the BackEnd

First step I took was to set the backEnd side of this project up. Just like the previous projects I've worked on, I've done a little brainstorming, and came up with the necessary `has_many` and `belong_to` relationships. Once the models are associated with each other it was time to configurate the `controllers`. When rendering the `action methods` you must use `json` and anything that that's associated with class you must `include` it, because javaScript has its own way of receiving them. See in example below!

```
class UsersController < ApplicationController

    def index 
        users = User.all 
        render json: users, include: [:games]
    end 
		
end 
```

Not only those steps are necessary, you also need to navigate to the `config/initializers` and open the `cors.rb` file. 
Inside this file you will need to change the line of code that says `origins "www.example.com"` to `origins  "*"` this will allow your `HTML` file to access the information it will be receiving from javascript. 


## Building the FrontEnd

The second step, I approached was to build the FrontEnd side. First I created the `HTML`  like so. 

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SomeTitle</title>
</head>
<body>
    <main>

    </main>
</body>
</html>
```

Next step I jumped to was create some `javascript`. I started with building the classes and used the `constructor` to create the `props` that match with `models` attributes, so they can work together. In order to `initialize` in the javascript's `class` you must use the keyword `this` that keyword is also used for other task as well, but it will not be discussed here. See the example below!

```
// This is a JavaScript Class

class Button {
    static all = []
    constructor({ id, name, sound }) {
        this.id = id
        this.name = name
        this.sound = sound
		}
		
	}
``` 

You are probably like what is `static all = []`, if you recall in `ruby` there was a `class variable` we always create, that was `@@all = []` we used this to collect all the instantiated objects, javascript follows that concept. 
