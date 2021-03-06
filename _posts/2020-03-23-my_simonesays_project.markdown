---
layout: post
title:      "My SimoneSays Project"
date:       2020-03-23 20:40:26 -0400
permalink:  my_simonesays_project
---


Let just start by saying this project was pretty fun, all the step I have taken worked pretty well. Taking one step at a time was the best way to approach it. First, create the backend and generate the necessary `rails` class. Second, create the frontEnd, this contains  `HTML`, `CSS`, and `javaScript` files. Last, in the javaScript files make all the necessary `iterations`.


## Building the BackEnd

The first, step I took was to set the backEnd side of this project up. Just like the previous projects I've worked on, I've done a little brainstorming, and came up with the necessary `has_many` and `belong_to` relationships. Once the models are associated with each other it was time to configure the `controllers` and set up the `routes` in the `config/routes.rb file`. When rendering the `action methods` you must use `json` and anything that's associated with the class you must `include` it, because javaScript has its way of receiving them. See the example below!

```
class UsersController < ApplicationController

    def index 
        users = User.all 
        render json: users, include: [:games]
    end 
		
end 
```

Not only those steps are necessary, but you also need to navigate to the `config/initializers` and open the `cors.rb` file. 
Inside this file, you will need to change the line of code that says `origins "www.example.com"` to `origins  "*"` this will allow your `HTML` file to access the information it will be receiving from javascript. 


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
		<script src="Button.js"></script>
			<script src="ButtonsAdapter.js"></script>
</body>
</html>
```

The next step I jumped to was the file Button.js for `javascript`. I started with building the classes and used the `constructor` to create the `props` that match with the `model's` attributes, so they can work together. To `initialize` in the javascript's `class` you must use the keyword `this`. That keyword is used for other tasks as well, but it will not be discussed here. See the example below!

```
// This is a JavaScript Class

class Button {
##     static all = []
    constructor({ id, name, sound }) {
        this.id = id
        this.name = name
        this.sound = sound
		}
		
	}
``` 

You are probably wondering what is `static all = []`? If you recall in `ruby` there was a `class variable` we always create, that was `@@all = []` we used this to collect all the instantiated objects, javascript follows that concept. Once all the necessary objects and functions are set it's time to create a javascript class `adapter`. Here is where you will `fetch` for the URL you will pass in your `index.js` file like so.

```
class ButtonsAdapter {
    constructor(url) {
        this.url = url
    }
    fetchButtons() {
        fetch(this.url)
            .then(res => res.json())
            .then(btnObj => {
                for (let btn in btnObj) {
                    let newBtn = new Button(btnObj[btn])
                    newBtn.fullyRender()
                }
            })
    }
}

```


## Iterating in Index.js

Last, but not least, iterating  through code in your index.js file. Remember those classes that were to create instances of an object. Here is where you will be calling for those and giving them specific tasks. To get started first you need to instantiate the ObjectsAdapter and give it a URL with the code `let obj = new ObjectsAdapter(http://localhost:3000/objects)`. By creating this line of code you have made the ObjectsAdapter `fetch` for the URL `http://localhost:3000/objects`. When you call `obj.fetchButtons()` and check your HTML file on the browser you will see buttons objects appear. For there you can create a variable that  uses `querySelector` to get the `document` of these buttons. Once the objects can complete their task you can now decide whether to design your app with `CSS` or not. 

![](https://media0.giphy.com/media/30pjsLvNyaRY0eoE0b/giphy.gif?cid=ecf05e4728111151fbb3dcf61a885d50494b7ad4596a7cd7&rid=giphy.gif)
