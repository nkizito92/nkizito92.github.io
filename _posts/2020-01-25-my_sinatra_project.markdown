---
layout: post
title:      "My Sinatra Project"
date:       2020-01-25 00:34:22 -0500
permalink:  my_sinatra_project
---

## Graduate's Goals

Working on this project was a lot of fun. During the process, I've learned many tricks and trades that will be quite useful in the future. The first trick I learned was how to check to see if every code is work without the need for testing.
Second, was how to bypass some features through a hack sort of. Third, was how to secure your code properly so no outside source can come in from the back door.

While, I was working on this project, I was wondering how I could use a debugger called `pry` to check and see if my line of code is working. Well, the first thought that came to mind was run `rspec` in the terminal. 😂😂 that didn't work because there is no test created in the `spec` file to check specific code. My next thought was maybe in one of my get request I should put `binding.pry` and run `rackup` or `shotgun`  to see if that will work. 🧐 Getting closer, now all I need to do is go to the browser and type the route I place the code `binding.pry` in.

![](https://media3.giphy.com/media/dxVdo4ca7FkME/giphy.webp?cid=790b7611f6ab58ddcf045b4d05cfab84d0f4378999317a51&rid=giphy.webphttp://)

### I have succeeded!!
Now that I have discovered how to debug my code everything started to fall in place more efficiently.

## Securing The app

There are some hackers out there, so you need to secure your application. Knowing this I have learned how to make it quite a task to hack into my application. If your app involves a user creating accounts and posting new tweets, or in this case "Goals" you need to know how 'session' works. There is a gem called `bcrypt`, this gem is a password hashing function, it's job is to change your created password "Hello_is_my_password" into
`"$2a$12$HghvcXmaTwzNo6qvTxD9NO6fwRIWpHqieWh3lpkZ5n24UH.Ugpn4O"` yeah you get the picture. There is no way anyone can guess a password to an account if it's that long. Before you can use `bcrypt` tools you'll need to go to your `models` folder and add `has_secure_password` in the file that will hold the values for a user's account. There are other tasks you must do to get 'bcrypt' working. Those are making a file in your `db` folder to create a users table with the columns username and `password_digest`, so you can run `rake db:migrate` in the terminal and create the the database.

## Hacking and Patching
![](https://media0.giphy.com/media/xUPGcxUB7uurcg0jLi/200.webp?cid=790b76113f819e9ecc2df42816dbc66c98a53430019bf0d5&rid=200.webp)

OK, now that the app is ready, let's run it using `rackup` and print the localhost link in the browser. Alright, everything is working as intended, but what if a hacker tries to edit or delete another user's post?
What if someone creates an account with the same username? These are things I didn't take into account. It was not until I asked someone to show me how you can get to the back door of my app.

![](https://media0.giphy.com/media/l2SpSS9zb15gtyn0A/200.webp?cid=790b7611e37acc2c0947a4394cd04c891aa1f1f8ee00299c&rid=200.webphttp://)

How do you patch up those cracks and lock the back doors, so hackers will find it hard to sneak in?
Using the `if statements` is a good start to create restrictions, but there needs to be more. Remember earlier I mention the  `session` and the `bcrypt` tools, well its time to put them to work. First, I created helper methods `logged_in?` and `current_user`. The current_user method contains the `session` that is given a `user_id` or removed as soon as the person signs in or signs out. Current_user's goal is to find the session's `user_id`. The `logged_in?` method is used to check `if` the person is `logged_in?`. It also contains a session, but it's only goal is to see if the session has a user_id. With all these tools and helper method you can create real security for your app.
