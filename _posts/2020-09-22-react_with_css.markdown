---
layout: post
title:      "React with CSS"
date:       2020-09-22 21:58:12 +0000
permalink:  react_with_css
---


For my React project, I chose to use one of my previous app desgin project. Grain Up encourages users to work towards an ideal economic future by visualizing financial goals as grains to be nurtured. At the same time, we function similarly to the Free Rice program through our collaboration (with World Food Programme) in providing food to those in need, users are motivated to look further from the self and to save with an enthusiastic heart rather than with dread.

However, with the time limit, I have to narrow down all the functionalities I have from my original design project. Also, I made the funtions much more simple than before, and I limit the garden to show just one plant(Your goal). Other than that, a plant still has many water entries :)

After setting up my backend, I started frontend by creating all the the files I need and planning out what will go where in each files. I have my home and app as my container, where home will contain render the main plant view and app will be containing routes. Alongside with my two containers, I broke plant views into: empty plant view, seed view, half plant view and full plant view into their own components where each of them will return their own information of that specific page.
I also added some conditions in my renderPlantView function just to make sure that once the total water hit certain amount, it will return the different plant view, which I think it's really interesting for me.

Besides setting up all the files such as action files, which contains all my fetch actions and reducers, which specify how the state changes throughout the application. I spent alot of time on styling my whole app, from that I learned alot such as making circle button, put icons in the button, have hover effect, placing div block at certain place I want on the interface, making background to be 100vh and vw, it goes on and on. I'm happy with the progress I've made in terms of getting this app working and looking pretty, and how much I've accomplished in CSS, even though CSS isn't the main part of the final project! But I had fun.


