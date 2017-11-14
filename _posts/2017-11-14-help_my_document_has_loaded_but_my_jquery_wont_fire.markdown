---
layout: post
title:      "Help! My Document Has Loaded but My jQuery Won't Fire!"
date:       2017-11-14 15:34:37 -0500
permalink:  help_my_document_has_loaded_but_my_jquery_wont_fire
---


Ok quick disclosure before I jump into my project: I really did not like JavaScript while I was learning it. After working almost exclusively with Ruby/Rails moving into JavaScript was jarring. Ruby is such a sweet, nice, easy-to-anticipate language compared to JS. I must have rage quit 20+ times going through my lessons. I felt like I was playing guessing games half the time I was writing code. There didn't seem to be any patterns or rules, it was just "run it and see if it works! Ok great it does! Not sure how, but we're moving on!" For someone like me, this was extremely frustrating. I once again felt like I had no idea how to code. 

![](https://pics.me.me/most-people-rejected-his-message-javascript-sucks-shut-up-they-28664127.png)

*#truestory*

Fret not, there's a happy ending! After finishing the JS section and moving onto React I was able to see the patterns emerge. I could visualize how the pieces connect. I finally understood what the actual goals were when learning JS. Or maybe I just became accustomed to the nuances of JS. Either way, I stopped raging and started rolling my eyes when my code failed. 

**On to the project**

So now we're here. I feel pretty comfortable with JS, no longer intimidated by it or distracted with anger. I know how to mess about with the code enough to deal with JS's fussy and seemingly unpredictable behavior. I began working on refactoring my previous Rails project to include jQuery and AJAX! How exciting! The Rails project I've been working on is a private library to help users manage their video game collection. You can find it here: [](https://github.com/FreeBreadsticks/game_library)

Now comfortable with JS syntax and API concepts, I didn't struggle too much understanding how to approach meeting the requirements. However, this didn't prevent me from running into trouble(of course)! The first thing I attempted to get working was displaying a user's screenshots. Everything seemed to be fine until I noticed something strange was happening. When clicking the link to bring you to the user show page it would initially work as expected and the images would load on the screen. However, if you clicked the link to the user show page again the images disappeared. In fact, the only way to get them to come back was to refresh the page.

..Uhhhm...what??

![](https://media.tenor.com/images/86eb7c00905ba5fa58b0e0bc7c7c7486/tenor.gif)

*my reaction 99% of the time when working in JS*

**Tackling the problem**

So, of course, I originally chalked this up to JS being the cheeky language it is. I incorrectly assumed it was some stupid syntax problem. So, like a good developer, I began googling around. Interestingly enough, there were plenty of people with the same issue. However, the core of their problems centered around their syntax being incorrect. After double and triple checking my code, I couldn't find any syntactical errors. So, I turned to a friend. When in doubt, pair program it out! (I’ll see myself out.) After spending far too much time rewriting the same function about 30 times we still came across the same issues. After getting literally no where, we decided to take a break and come back to it. 

Naturally, I couldn't let this go. I kept scouring the internet. "I'll be damned if I let this problem beat me!" I thought to myself. Thanks to my incredible capacity to be unrelentingly stubborn, I have achieved mediocre levels of programming skills. Eventually I stumbled across a post on StackOverflow with the answer I needed. And let me tell you, it was one of those moments where you say to yourself "You have got to be KIDDING ME!"

![](https://i2.wp.com/gifrific.com/wp-content/uploads/2012/06/Michael-Scott-angry-stare-at-toby.gif?ssl=1)

TO RECAP:  
1. Images load first time you visit the page.
2. Clicking the link to the same page, images no longer load.
3. Refreshing the page, images magically load once more.

SOLUTION:
Remove `//= require turbolinks` from `application.js`

Wouldn't ya know it! As soon as I removed that little line everything worked as intended with zero issues. All that time spent refactoring something that was already correct. All that time trying to pinpoint the issues. All that time googling and sifting through irrelevant solutions. All that time spent trying to figure out what's wrong because it's understood that JS can behave strangely and have unintended errors that can be difficult to track down (A piece of me can't let go of the resentment for JS).

Still. I solved it.

You know why?

![](https://media.sticker.market/gif/music-video-kelis-bossy-58c1b5dd2dcb763c6d6c533a-g.gif)

