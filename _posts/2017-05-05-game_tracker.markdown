---
layout: post
title:  "Game Tracker"
date:   2017-05-05 18:31:58 +0000
---


### A simple Sinatra solution to keeping a neat library of your current games!


![](http://i.imgur.com/eas3xwg.png)

Going through Sinatra wasn't as difficult as I had originally anticipated it to be. CRUD for the most part is a straight forward concept and as long as you follow conventions there isn't too many issues with what you're attempting to build. What made it even easier for me was all the lessons building up to this point. Instead of just being handed the Sinatra library and shown how to use it, I was taught how all the pieces work together before even seeing Sinatra. I truly appreciate the knowledge I have of how things work through the OO Ruby sections of the course. It has made me waaaaay more confident in my coding ability when working in Sinatra. When errors come up I am able to read and understand them much more clearly because I am very familiar with how objects work in Ruby now. It's very satisfying to feel that way, as before I was terrified of errors. I recommend anyone learning Ruby or any Ruby libraries to get intimate with object creation and relation. It will make your life easier.

### On to my project

I think the hardest part for me always is deciding what I actually want to do. I never want to just make something for the sake of passing my course. I want to make something I or someone else might use! Possibilities, of course, are endless. I ended up settling on a video game library of sorts. A user can sign up, login, and add games to their personal library. 

![](http://i.imgur.com/dJkfEhT.png)

Getting my file structure correct was the only thing I was truly worried about. So the first thing I did was set that up. Having the proper directories in place gave me a nice road map as I went on creating the app. Understanding MVC and how it works is essential in putting this together. I feel I had a pretty firm grasp on that so hardly ever did I feel completely lost. It really was just a game of making sure my actions had controllers attached to them so everything worked properly. Having a solid understanding of Sinatra and CRUD allowed me to play around with my CSS! I had a good time making it look pretty :)

At one point I did get tripped up on an error. My getter/setter methods did not appear to work at a certain point in time. This was pretty upsetting because I thought I had somehow messed up the database and classes that went along with them. Thanks to Avi, I was able to pinpoint exactly where this issue stemmed from. A different method I had written was returning an array, not the object which I had intended for it to do. Once I saw that I knew how to tackle it. Lesson learned - be very aware of what your methods are returning! It could come back to haunt you if you don't check that they are doing exactly what you want them to do.

After the minor hiccup things glided along and the project fell in place rather quickly. So quickly in fact I was a little sad when I realized I had completed it and done just about everything I felt comfortable with. However, I do plan on adding more features to this little app as I really have had a great time with it!

If you're like me and play lots of games, so many that you have difficulty keeping track of them, check out my app! It may prove useful to you. You can find it here: https://github.com/FreeBreadsticks/game-library-sinatra

