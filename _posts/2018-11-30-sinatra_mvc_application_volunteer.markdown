---
layout: post
title:      "Sinatra MVC Application: Volunteer"
date:       2018-11-30 22:47:50 +0000
permalink:  sinatra_mvc_application_volunteer
---


I created a Volunteer application for my Sinatra Portfolio project to promote volunteerism and to create an entry management system where volunteers could be rewarded by local businesses. The more a volunteer commits entries for each volunteer activity, the more points they accumulate, which can then be rewarded by local businesses in the form of free items or discount coupons. This idea was in part motivated by a neighborhood woman that I see picking up trash every morning on her way to work. I was excited about the idea of building a web app that encouraged volunteerism for all types of volunteer activities, especially those activities that occur day-to-day, like shoveling snow out of your neighbor’s driveway. Sinatra is a domain specific language for building small dynamic web applications with Ruby. My general process was as follows:

* Create a project folder and stub out the app structure using the Corneal gem, based on the Model-View-Controller architectural pattern. 
* Add necessary gems to my gemfile including test and development gems and run bundle install. 
* Decide which controllers were needed and mount them to my config.ru file to load my environment. 
* Create a flow diagram on pen and paper that shows the direction and relationship of my overall application structure: Controllers, models, database values and views. 

The User model has many volunteer entries. It also runs validations on the user data for the user’s name, email address and password. Placement of validation code, within the controllers, models or views determines whether the validations occur on the client or server side. Sinatra flash messages were used to provide feedback to the application user when information is processed, whether their request was successful or not and sometimes, to direct them to re-enter their data if invalid data was submitted. Sinatra flash is a helper method that uses sessions to store data between requests. Within the session object is a session_id that lives within the cookie for the life of a session.

 The controller authenticates the password and uses the BeCrypt gem and has_secure_password method to disguise the user’s password and make sure only valid data persists in the database. The Entry model shows how entries each belong to a user. 

The User controller creates new instances of users and through active record associations, persists only valid data in the database. The entry controller creates new instances of entries. The User and Entry controllers each inherit from the application controller and contain the  create, read, update and delete HTTP methods of CRUD. 

Then I sketched diagrams of the user story- how I want a user to perform actions on the page and the order of RESTful routes that allows them to move through the application, generally based on 2-3 choices. This process determined how I input my redirect and render methods and in what order I placed them within my controllers. As I started building out my controllers, I tested each feature both within the terminal via tux or pry and/or within the browser via shotgun. 

In terms of my database, I wanted a user to have a username, email and password and my entries to have a title, location, date, description, user_id and timestamps.

Lastly, I used a HTML5Up responsive design template. I created a public folder where Sinatra knows to look for all static Javascript, CSS files, and image files by default and merged the index.html file content into my layout.erb file within my views folder. I trimmed the template to the bare bones and slowly added features that I thought would enhance the user’s experience. I added a sidebar with clickable links that show the full functionality of the application. After a user is logged in, a new sidebar item appears, which was created with a conditional statement in the layout file. This link brings the user to their own Entry Show page, where they can view accumulated points and timestamps such as created_at and updated_at information. I learned so much working through this application build and I am pleased with the final product. I hope to fully build out the application in the future.
