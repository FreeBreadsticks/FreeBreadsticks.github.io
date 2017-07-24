---
layout: post
title:  "Game Track - a Rails Project"
date:   2017-07-24 00:48:15 +0000
---


For my rails project I decided to make a video game library. Users can add and manage games that they own. This would be useful for someone like me who has so many games I can't keep track!

Before I even opened an editor I wanted to plan everything out as much as possible so I could keep my code as tidy as possible. I went over the requirements and planned out my database according to what I thought would be the easiest and most manageable way to meet them. I decided a user would have_many games, a game would belong_to a user. I also decided that games would have_many screenshots, a screenshot would belong_to a game and users would have_many screenshots through a game. I decided this would make the app robust enough to work completely and satisfy the requirments!

After planning was through I knew it was time to get my hands dirty! I went ahead and got a new Rails app and built out the User database first with Devise. Using Devise allowed me to easily meet authentication, user creation, and session requirements! There was a minor adjustment I wanted to make to the Devise User model, however. I wanted the user to also have access to a username attribute. I realized quickly that even though username was an attribute in the database as well as a field on the form, it wasn't being saved. I googled and figured out that I needed to make a params sanatizer that told Devise to allow the username. Once I had that working I moved on to some basic design structure. I used Bootstrap for my design. I knew this would allow me to create a nice, clean design that wouldn't be to difficult to put together (thanks Bootstrap!).

Next I moved to working on the game model. I decided games would have a title, description, rating, user notes, and the ability to note wether or not you have completed the game. Once I had a games table set up in the database I went ahead and moved on to routing and controller. I set up the controller with RESTful routes for the game and the views to go along with it. It was at this time I also created a route, controller, and view for a user show page. I then set up a form for the game model. Thanks for form helpers I had it working in no time!

It was now time to work on screenshots. I looked around for a good image uploader and found Paperclip. I followed the instructions on Paperclip's github page and got it working rather quickly. I knew I wanted screenshots to be a nested resource in games. So now it was the hard part of attaching the screenshot to the game model via a form. I did some research on how to best handle it and I modified my routes so screenshots would be nested under games. I also wrote a custom attribute writer in the game model to handle the submissions for screenshots. I also modified game's strong params to accept screenshot attributes. After messing around for a little bit I got it working and was happy with it. Now it came to taking all that information and displaying it in an attractive manner. 

I decided on the user show page I would iterate over the games displaying the first screenshot, title, description and a link to the game show page. On the show page you would be able to see all the game's detailed. It is here you can also see all the screenshots you uploaded for the game as well as add a new one. This new screenshot form I decided would be more attractive if placed in a modal. The modal was a little difficult to work with at first but I did end up getting it working and looking nice! 

I decided at this point that I wanted to spruce up the user show page a bit more. I went ahead and built set up a flow that would display completed games in a green box and uncompleted games in a blue bow. I thought this would be a nice touch for users to easily see what games they have and haven't completed. I also decided it would be nice if they could go to a page and view only completed games. I went ahead and built a class method that pulled only completed games, a controller action, and route to handle moving the user to this info. I used the partial I created for the user show page to make the completed games page. It looked nice and worked out quickly! 

At this point I felt I had overcome a lot of different issues and was happy with what I had completed. My app looks nice and is useful! If you're interested you can find it here: https://github.com/FreeBreadsticks/game_library 


