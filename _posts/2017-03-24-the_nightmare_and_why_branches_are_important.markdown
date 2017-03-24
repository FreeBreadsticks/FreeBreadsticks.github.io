---
layout: post
title:  "The Nightmare and Why Branches Are Important"
date:   2017-03-24 12:51:51 -0400
---


This past week I encountered one of the most terrifying experiences in coding. I had a complete working project, a project I had spent hours building and designing and cultivating. One that when it was complete, I couldn't have felt more proud! I had created a CLI Data Gem, one that scraped information from a website and listed it out for the user. I had never done anything quite like that and I did it all on my own from scratch. I was on top of the world. I got this coding stuff! I even got as far as publishing my baby gem to Ruby Gems! (which you can find here: https://rubygems.org/gems/orlando_events )

**In an instant it changed.**

I pushed my code back into git and then ran my program one last time just to bask in the beauty. This is what I was greeted with:
![](http://i.imgur.com/q0gqFRH.pnghttp://)

I stared at my screen, mouth agape.

`"The validation error was 'orlando_events-0.1.5 contains itself (orlando_events-01.5.gemspec) check your file list"`

Ok that's weird but maybe a bundle install would fix this?
![](http://i.imgur.com/OE8e3VZ.png)

I was horrified as I felt my world crashing down around me. I should have known not to get too cocky. "Ok, fine, I'm sure this happens all the time!" I said to myself as I opened up google. I started going through some of the results, even out the gate it really didn't look to promising. I went through a couple of posts and they all seemed far more advanced than what I was capable of and I wasn't sure exactly how I was going to end up tackling this. I got scared and decided on a different route. I can rollback to one of my previous working commits! I knew I had a working push from a day ago so I figured that would be the place to start and it was something I could wrap my head around. I some how got the idea I would work in two separate project states as well. Considering I wasn't sure exactly what would fix this I would roll back one project and keep another at the broken state. I ran 

`$ git push -f origin last_known_good_commit:branch_name` 

and I ended up getting a working project. First crisis averted - at least I had something (THANK YOU GIT!!!). This wasn't enough.

**Why did this happen and what exactly is this validation error?**

I compared my broken gemspec to the working gemspec. I didn't see a difference in the code. This infuriated me. Why the hell did it break in the first place? Why would it play with my emotions like this? I just couldn't figure it out. I went back to google and found someone having a very similar issue to mine. So I started following their instruction. The cause of the issue was a file: orlando_events-0.1.5.gem. Removing this file, the post said, will fix this issue. So I ran

`$ rm orlando_events-0.1.5.gem` 

Tried running my program and..
![](http://i.imgur.com/q0gqFRH.pnghttp://)

I put my head down on my desk and sighed. I stared at my code. I compared my broken project to the working. I checked to see if the file I removed was there. It wasn't. I tried running

`$ rm orlando_events-0.1.5.gem`

again and of course it let me know that no such filed existed.  How could it even be referencing a file that wasn't there!?? I was close to giving up when I found one last blog post that seemed to encounter something similar. There was one more step that he included. 

`$ git rm orlando_events-0.1.5.gem`

 I crossed my fingers and ran my program again...
![](http://i.imgur.com/UXE0DQU.pnghttp://)

**HALLELUJAH!**

It worked my program ran again and it was looking just fine. I breathed a deep sigh of relief and reminded myself to continue to be humble when it comes to coding. At the end of the day, I'm not entirely sure how this ended up happening. I definitely know now that I need to get more comfortable creating branches when coding on working projects. Perhaps some day, a kind soul will stumble upon this blog and will show me where this happens and how to avoid it. I truly hope this helps anyone encountering a similar issue.
