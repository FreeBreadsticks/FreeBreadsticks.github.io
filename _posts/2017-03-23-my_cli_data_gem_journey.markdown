---
layout: post
title:  "My CLI Data Gem Journey"
date:   2017-03-23 18:20:26 +0000
---


When I first read about this project I will admit I was a bit intimidated. However, I have had prior experience with larger projects in Ruby so I felt that I was capable and I could probably do it. Knowing that I would have help from the people at Flatiron if I needed it also eased my nerves. I also had always wanted to learn how to do something like this so I was excited to see if I could figure it out! 

**Starting Out**

The first hurdle would be deciding what exactly I was going to scrape. I will admit I wanted to stick to something a bit more simple because I felt I would gain a firmer grasp on the ideas and subjects at hand. I ended up choosing a Downtown Orlando Events page. You can find the page here: http://www.downtownorlando.com/future/events/ . I live downtown and am always looking for fun stuff to do around town so I thought this would be perfect for me! I opened up the inspector and started investigating the CSS of the page and found that it was perfect for what I needed! 

**And the Fun Begins**

Now that I have chosen a site to scrape from I was ready to get building. Before I opened up my editor I gave some though to how I wanted this gem to work. I looked again at the website and how information was displayed there. I decided I would list the months available. I would then allow the user to select a month and display a list of events for that month. Each event would have the date, the title, and the location. Perfect! 

It’s true that the hardest part was staring at a blank text file and not knowing what to do first! To help me get a strong start I watched a video lecture by Avi, this proved invaluable (thank you Avi!). Using the video and some googling I learned of the gem install bundler and the bundle gem commands. This created the directory that I worked in. It gave me the skeleton for which I could build upon and organized files for me in an extremely useful way! 

**The CLI Class**

Following Avi’s lead I too began working on my CLI first. I really believed this helped dictate how I built my other classes and helped me to avoid superfluous code. Here’s what I decided my CLI would do:
* welcome users
* display list of months
* allow user to pick a month via numerical input associated with the month
* list the events of that month
* allow user to list months again
* exit the program when user is done

I first created a call method. This method is essentially used to start the program by calling the other methods. list_dates is the first method I build, this method will be responsible for listing the months available from the website. I then build a menu method which allows a user to pick a month and the method would return a list of events from that month. I started off hard coding this information just to make sure it looked right and made sense. I also created a method called goodbye responsible for ending the program and telling the user goodbye. 

**The Scraper Class**

With this outline I knew what the rest of my program was required to do! So I got started with the Scraper class. I require nokogiri and open url in order to read the information from the website. The first method I built was scrape_dates. scrape_dates accepts a website url as an argument and scrapes desired information from that site. This is where I am able to pull the name of the month and the month’s event page url. I return this information in an array of hashes. The hashes contain each month’s name and url in key value pairs.  

The second method I built takes in an argument of a month’s url and scrapes the information from this page. It is here I create an array of hashes once again, except this array contains hashes the month’s events. 

Back in the CLI I create a method make_months. This method is responsible for creating the months by calling Scraper.scrape_dates on the downtown Orlando page and sets it equal to a variable; months_array. It is here I realize I will need another class to hold the information generated from my Scraper class. 

**The Event Class**

This class is responsible for handling the information from my Scraper class. I first create a custom constructor, self.create_from_collection, that accepts the array months created in the make_months method. This method iterates through the array and calls Event.new on each month.

In initialize I accept a month hash which I iterate through and set the attr_accessor items equal to the hashes values using self.send “{key}=“, value. I have also create a class variable @@all = [] and push the newly initialized month into it. I build a self.all method that exposes @@all because I know I will need to access this data in order to print it. 

Back in the CLI I am able to go into list_dates and make use Event.all. I set Event.all to an instance variable @dates. From here I am able to iterate through @dates and print out the names of the month objects! Success I now do not need to hard code the Months and am able to print them out dynamically. Now I am ready to tackle listing the events.

**The MonthEvents Class**

I realize I need to somehow list events associated with each month. I struggled a great deal at first on how I would tackle this. I knew I had the information but I was unable to print it out the way I desired at first.  I decided making a MonthEvents class would be the best way to abstract the information and to make it more dynamic. 

In Event I create a method add_event_details that accepts an array of hashes of event details that is created by the scrape_event_info method from the Scraper class. This method will iterate through each month and call MonthEvent.new passing in the event hash and itself. 

MonthEvent initializes with a hash and an object. It’s here I make use of self.send once again setting the appropriate attr_accessors to the values in the hash. I also set the month of MonthEvents equal to the Event object passed in. This allows the two classes to interact! I also set an @@all class array and push each new MonthEvents object into it. I also expose this data using the self.all method. I modify the month= method to set month equal to the Event object and then call add_events on the Event object passing in itself. 

 add_events lives in Event class and it takes in a MonthEvents object. It’s here I see that I will need a instance variable of events to contain this information. So I modify the Event initialize to include and empty array @events. Back in add_events I push the MonthEvent object into the @events array. Whew! That was tough but it is doing everything I need! 

Now we go back to the CLI. Here I create another method called add_attributes_to_months. This method iterates through Event.all. For each month we iterate through I call Scrape.scrape_event_info passing in the month’s url. I set this equal to an events variable. I then call add_event_details passing in the events variable. This is the last part that creates all of the information necessary to print out the information to users in an easily readable way! 

In the menu method I iterate through the specified month’s event array and print out each event’s details! 

Hooray! Everything has finally come together and I am able to see all of my hard work in action. One of the best feelings in the world is seeing your code working exactly how you want it to! I am able to successfully list the available months, choose the month I want more information on, and then print out the events associated with that month. 

**Finishing Touches**

Once I had everything working it was time to go in clean up some code, and prettify my program’s output. I made use of the colorize gem and colored the outputs to help make it more readable as well as attractive. I fiddled with different ways of outputting the info and what colors I wanted to use until I was satisfied. And satisfied I am!

I really had so much fun with this project. I couldn’t be more proud that I was able to do something as neat as this from scratch on my own. I am excited to do more work like this in the future and I feel as though doors have already begun to open to new ideas!



