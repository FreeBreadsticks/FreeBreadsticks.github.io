---
layout: post
title:      "React Router"
date:       2017-12-22 19:55:54 +0000
permalink:  react_router
---


React Router can be a tremendous help when it comes to navigating your React app. Much like Redux has a single source of truth for your data, React Router is the source of truth for your URL. In this post I will go over a couple of tips on how to use React Router in a web app.

**Installing**

After you have your app set up you will need to install `react-router-dom`  you can do this by running

`npm install --save react-router-dom`

The next thing you will want to do is import React Router into your app:

```import { BrowserRouter as Router, Route } from 'react-router-dom'```


From the Redux docs: 

> In a React app, usually you would wrap `<Route />` in `<Router />` so that when the URL changes, `<Router />` will match a branch of its routes, and render their configured components. <Route /> is used to declaratively map routes to your application's component hierarchy. You would declare in path the path used in the URL and in component the single component to be rendered when the route matches the URL.
> 

**Using React Router in Your Project**

Let's take a look at an example using a project I worked on:

![](https://i.imgur.com/X4dHjB7.png)

Let's break down how this works:

`<Route exact path="/" component={Home} />` would be considered my index route/home page. As you can see I have set the component equal to Home. Home is a component I built to display some basic information about the page. In order to make sure this works you need to import the component at the top similar to the way you do with React Router.
Booting up the app will take you directly to the home page and as long as you have imported everything properly the Home component will show up!

**How to Link a Route**

In my project I have a navbar set up to get around my little Pokedex app.

![](https://i.imgur.com/cKopSS4.png)

Let's take a look at how you can set up Links that work with your Router.

From the docs:
> React Router comes with a `<Link />` component that lets you navigate around your application. If you want to add some styles, react-router-dom has another special `<Link />` called `<NavLink />`, which accepts styling props.
> 

In my project I have component called Navbar I specifically set up to hold my links:

![](https://i.imgur.com/DDaORS2.png)

You will note that I imported `NavLink` into this component, this is needed in order to use React Router for Links. You will also note that imported `Navbar` into the component that holds my routes! 

`<NavLink to="/" activeClassName="active" className="navbar-brand">Home</NavLink>` This is the Link that matches up to the Route I set to the Home component. All you really need to do to get the Link working is make sure `to="/someurl"` is the same both in the Route and the Link. It's really as simple as that! With this hooked up everything will work nicely and as expected. Easier than you thought, huh?

**Can I make a Link into a button?**

Of course you can! It's just as easy. Make sure to import `import { Link } from 'react-router-dom';` at the top of whatever component you are looking to have the button in. Within the render function of your component you can place the Link and add styles to it. Here is an example of how I used this method:

![](https://i.imgur.com/lB9kF1x.png)

Again, all you really need to do is make sure you have a Route set up that matches the Link path that you set inside of your component. Apply stylings how you see fit and you are good to go! In my particular project I used a combination of Bootstrap and custom CSS for styling.

**How can I Link using RESTful Routing?**

If you're looking to link specific pieces of data and have a component populate based on params in the URL React Router makes this easy as well! 

In my Pokedex app I have a list of Pokemon. I'd like to be able to look at each Pokemon on their own page as well. Let's take a look at how I have it set up in my project:

First I need to set a Route that follows REST conventions:

`<Route exact path="/pokemons/:id" component={PokemonPage}/>`

So here I am setting a path `/pokemons/:id` that displays my PokemonPage component. The `:id` is a placeholder value that I can set when setting up links in a component. 

When linking in your project, always be sure that you have properly imported the component needed from React Router, in this case it is again: `import { Link } from 'react-router-dom';`.  Here is what the Link looks like in my project:

![](https://i.imgur.com/bxpZnwd.png)


As you can see my PokemonCard component is receving the props `pokemon` from there I am able to retreive the `id` and set it inside the link! Clicking on the link will now bring you to the PokemonPage component. However, there is one last thing: we have to make sure our PokemonPage component knows what pokemon it is referencing since we are not passing props into a component.

Using Redux with React Router allows you to retrieve data from params in the URL! Let's take a look at how I have it set up in my project:

![](https://i.imgur.com/dtne5kS.png)

As you can see, using `mapStateToProps` allows me to search the current pokemons from state using the `id` passed in the URL. If a match is found I return that pokemon. I then pass that pokemon as props to my component. PokemonPage now has the correct pokemon to display! 

**Can I redirect to a page from within a function?**

I asked myself that question while working on this project. What I wanted to do was when you successfully submitted the form to create a new pokemon I wanted to redirect back to the list of newly updated pokemon! Doing this was actually very simple once I was able to sift through tons of overly complicated examples. 

I'll be honest, I'm not %100 sure if this is even a React Router thing as you don't need to import any React Router components into your file. My form submission calls a method which then calls a different method on success. Here is what it looks like: 

![](https://i.imgur.com/3ZsHhzg.png)

All you need to do is call `this.props.history.push('/your-url-here');`. It really is as simple as that! 

If you are interested in taking a look at my project and I how I did things you can find it here:
https://github.com/FreeBreadsticks/pokedex



