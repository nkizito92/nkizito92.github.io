---
layout: post
title:      "My ZapChat Project"
date:       2020-04-27 13:09:38 -0400
permalink:  my_zapchat_project
---


## by Kizito Njoku

Man oh man this React project was a real doozy, it was really difficult to get used to all the syntax when I was getting started with the React framework itself. After some practice, I learned enough to start working on this project. Luckily, I applied the same tactics used in my previous project. These where to start with the back-end, setup the appropriate relationships between the models, work on the front-end one step at a time, and finally, add some design to the project after all the functions are working. 


### Working On The BackEnd

Like the previous projects with Ruby and Rails, the first step is to brainstorm and figure what the appropriate relationships will be amongst models. Once those are settled you can create the Ruby and Rails backEnd with `rails new <You app name> --api`. When the terminal is done creating it `cd` into your rails API and make the necessary resource with `rails g resource <The Model> message:string` to create a model along with the routes and table that will be migrated. 

![](https://media3.giphy.com/media/l4FB5dgbc21nQPKhy/giphy.gif?cid=6104955e543f87b79e6cb083ac08742a8f264fe3fddb8d86&rid=giphy.gif)

After the migrating is done, next is to work one the controller's actions accordingly like so:

```
class ChatsController < ApplicationController
    before_action :sleeping, only: [:create, :destroy]
    before_action :found_chat, only: [:show, :update]
    
    def index 
        chats = Chat.all 
        render json: chats, include: [:guest, :comments]
    end 
        
end

```

### Working On The FrontEnd

When working on the front-end the first step that must be done is to run `npm init react-app your-app name`. This will set up all the necessary tools to get started. After this, depending on the number of components you have you'll want to also run `npm install redux && npm install react-redux`. These npms make it very easy to grab specific data from the `store` whether you are in a `child component` or `parent component`. Next, you need to run `npm install redux-thunk` so you can have access to the middleware if you decide to let your app `PATCH` or `DELETE` from the dataBase. Once all of these npms have been installed there will be `importing`  in top-level or App component. In this component you will need to `import React, {Component} from "react"` for each `class component` like so: 

```
  import React, {Component} from "react"
       class SomeClassComponent extends Component {
            render() {
                   return {
                       <div> Your first class component!! </div>
                     
                     } 
                
                }
         
         }
    
```


Alright! We have a component that uses react and renders an element. How do you get it to display data from the database? Well, first we will need to have containers that pass in  `props` to components, actions that `fetch` and follow the `CRUD`, and reducers that set the `state`  and automatically rerender components connected to it when the `state` changes. To get started it's a common practice to use the containers for passing data `fetched` from actions as props into components to keep some stateless. Ok, cool how do you get the container to pass in props for a component? When you create a component you need to `export default` it like so: 

​
```
  import React, {Component} from "react"
     class SomeClassComponent extends Component {
        render() {
           return {
             <div> Your first class component!! </div>
           
           } 
        
        }
     
     }
         
  export default  SomeClassComponent
```

and in the container, you need to import that component similar to the react, but without the curly bracket asking for Component. Then you can set it like an HTML tag and pass in the `props` with a made-up attribute like so:

```
  import React, {Component} from "react"
    
    import SomeClassComponent from "./components/SomeClassComponent"
    
     class SomeComponentsContainer extends Component {
        render() {
           return {
                     
           <SomeClassComponent   madeUpAttribute={this.prop} />
           
           } 
        
        }
     
     }
         
  
```

Since there's a prop inside SomeClassComponent, you can access this prop simply by typing `this.props.madeUpAttribute`. There's more task that must be complete like setting up your reducers, actions, and store, but will not be discussing that here simply for too many explanations. If you want to learn more about these this link may help [Redux](https://redux.js.org/basics/data-flow).

### Design The Project 

Now that the Front-End and Back-End are complete it's time for designing. When you create a `CSS` file for your project it's slightly different using the `link tag` in an HTML file. Instead of using the `link` tag you will be `importing` the file in you `App.js` file like so:

```
  import React, {Component} from "react" 
    https://simplemde.com/markdown-guide
    import "./style.css" 
      export default class App extends Component {
        
          render() {
              return (
                   <div> Your css file is now connect to all the components you imported here. </div>
                
                )
            }
            
        }
    
```

Awesome isn't it, that will conclude your hard work. 

### Summary 

In this project all the step you take is to first build your Back-End and make the controllers `render json: data` and if you half to `include: [:associated_data]`. Second, in the Frond-End create the top-level Component and pass in props to the child components and containers. Third, create your actions to describe to the reducers you created what is taking place. Last, designing your project with `css` to make it appealing to the user's eyes.

![](https://media1.giphy.com/media/MZ9nZGQn1nqBG/giphy.gif?cid=6104955e6914a419de2f881a7ddc91ca864dc2eff12611c3&rid=giphy.gif)
