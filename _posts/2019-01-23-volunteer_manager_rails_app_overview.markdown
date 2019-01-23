---
layout: post
title:      "Volunteer Manager Rails App Overview"
date:       2019-01-23 13:44:25 +0000
permalink:  volunteer_manager_rails_app_overview
---


This application is a mini project management system for the Volunteer community to have a means of managing volunteer projects, tasks and roles. (Yes, I am slightly obsessed with volunteering and finding more efficient ways to engage users in volunteer activities that cater to the last-minute sign-up and more introverted types, who are often disengaged with the volunteer community due to the extensive sign-up processes and large-scale group work.) In my application, a user can create an account or login via facebook to add each of these features open-source and open-access-style, though access and restrictions exist to discourage users from making too many changes.  

### Model Associations

Before starting to code, I sketched out my models and how they would relate to each other. Rails supports six types of model associations: 
* belongs_to
* has_one
* has_many
* has_many :through
* as_one :through
* has_and_belongs_to_many

A <span style="color:blue">resource</span> is information passed through a route that maps requests made with a HTTP verb to an action in a controller. Nested resources reflect our ```has_many relationship``` between models in the routes, and ultimately URLs. Nested resources occur when one model belongs_to another and in my application, roles ```belong_to``` a project and a user, and tasks belong to a role. This level of complexity is not easy to work with; however, I found a way to maintain these relationships, while simplifying and flattening my routes. Rails docs indicate that resources should never be nested more than 1 level deep. 

So I went from three levels to one and modified the top level from users to projects to better demonstrate my sketched relationships like this:

```
resources :users do
   resources: projects do
     resources: roles do
        resources :tasks 
     end
   end
end
```
to
```
resources :projects, :shallow => true do
   resources :roles
end

resources :roles, :shallow => true do
   resources :tasks
end

resources :users, :shallow => true do
   resources :roles
end
```
### Shallow routes
Adding the ‘shallow: true’ parameter to your nested resource will define routes at the base level, ```/roles/,``` for the base four RESTful routes — show, edit, update and destroy, while leaving the remaining routes — index, new, create at the nested level. Shallow is simplifies and flattens nested routes, which may not exactly be REST compliant, but as long as your associations are set up correctly, you don’t lose any information or hierarchy with the shortened overall paths from shallow routing as indicated below. Editing a role by ```:id,``` doesn’t necessarily make sense, because while roles belong to both projects and users, the ```role :id``` is independent of the ```project :id.``` When we want to edit or delete a role, it's relationship to project doesn't matter. A project can have many roles, so for example, project with :id 1, can have role with id: 1, 2, 3, etc..

Using ‘rake routes’, my role edit route went from:
```
edit_project_role 	   GET               /projects/:project_id/roles/:id/edit(.:format)
```
to the below route using ‘shallow’:

```
roles#edit		         GET	            /roles/:id/edit(.:format)
```

### Models 
I used ```rails generate model``` to create each model. Then I added attributes that I determined were necessary for each model, a scope method and a nested new and index route that relates to the parent resource. Along the way, I added necessary gems to my gemfile and few additional gems like ‘byebug’ to test my application as I built out each method and view page. 

### CRUD and authentication
I created a basic skeleton for all of my routes in my ```config/routes.rb``` file first allowing all CRUD actions in each model and later, limiting resources to only those necessary for each view. Following configuration, I added authentication via bCrypt and Omniauth and Facebook omniauth gems to allow users to login to my application using their Facebook account; facebook was chosen because it’s a common social media platform that volunteers use. My next step was to build out my controllers with CRUD actions; the only real difficulty in this aspect was making sure my nested relationships were embedded in my methods and associated routes were accessible to my view pages.

### Views
Back to the drawing board, I started manually sketching out my view pages on post-it notes with pen and paper. This allowed me to ‘feel’ the application layout, mapping and overall flow. I think what’s most interesting about building applications and also perhaps what’s most challenging is adding new functionality that has trickle-down effects. As much as I pre-planned my application on paper before I wrote a line of code and discussed the process with others, I made numerous changes after the build that caused me to re-think the integrity of my application and how I really wanted it to function. I used rails generators for each model and created a seed file to test my relationships. The ‘rake routes’ command allowed me to view all available routes. 

This is an early stage iteration of my project, which I will expand upon as part of my next portfolio project where I’ll integrate <span style="color:blue">Javascript, jQuery for the Front End and Active Model Serialization JSON Backend.</span>  

My biggest goal with each of these projects, is to go back and build out tests. Then, I’d like to add more interactive features that really engage a user and I’d like to do more research on built applications that function similarly, discovering what works and adding these types of features to my applications. Last, I’d like to scale-up and make efficient use of resources to allow my application to exhibit optimal speed. I recently listened to either a Syntax or CodeNewbie podcast where Wes Bos was describing very simple changes to CSS assets that can speed page load time by a few seconds.  I like to use projects as a way to explore new tools and methods that I read about on Medium or hear in code-related podcasts; this allows me the room to flex my learning beyond the curriculum.

