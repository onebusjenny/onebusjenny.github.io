---
layout: post
title:      "rake routes is my best friend"
date:       2020-02-05 08:25:48 +0000
permalink:  rake_routes_is_my_best_friend
---


rake routes is my best friend during the rails project. It's espeically helpful when I'm dealing with my nested routes, since sometimes it gets confusing when I'm entering either my user/:id/teas/1 or user/:id/tea/1. It gets wild because there are singular and plural difference, and normally that's when it matters, missing a "s" can cause a HUGE problem.

In my case, I got

    resources :users, only: [:index,:show] do
    resources :teas, only: [:new, :create, :show, :index, :edit, :update]
    end
	
as my nested routes, :teas are nested under :users. 

So when I enter /users/:id/teas/new, I'm creating my new boba.
/users/:id/teas, I'm at "My Boba" page, where it lists out all bobas I've created.
/users/:id/teas/:id, It shows the individual boba's information

Another thing I use rake routes for is to check my link_to path to make sure it matches where I want it to be link to.
For creating boba: my link for that is new_user_tea_path and for entering the Boba playground where it shows all the bobas all the users created will be teas_path. Here is when it's tricky for me, you can see new_user_tea is without an "s" and teas_path has a "s". I think it this way since the user is only making one new tea, so it doesn't have a "s" in it, and for teas_path, it's showing ALL THE TEAS every users made, so it has a "s" in it. So again, it's alwasy nice to have rake routes by your side so you will know for sure what it is. Also, you will be able to know if the routes you are want to know is existing or if there's something wrong with it. 

