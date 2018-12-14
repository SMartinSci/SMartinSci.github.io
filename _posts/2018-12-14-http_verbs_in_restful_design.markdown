---
layout: post
title:      "HTTP verbs in RESTful Design: within the MVC and API context of Modern Web Applications"
date:       2018-12-14 16:09:40 +0000
permalink:  http_verbs_in_restful_design
---

In my first portfolio project, I used Nokogiri and Ruby to scrape and parse data from a website to scope specific information I wanted from Fodor’s Global Food Festivals website and display it within a command line application to users. Users could interact with the data using my application, instead of seeing the full context of the page on Fodor’s website. My application used Model-View-Controller(MVC) architectural patterning to connect the three main parts of my application and display information directly to the user. Because of this, the design and associated data of my application relied heavily on an abundance of HTML code. If I had used an API, my code architecture and language itself would been designed to be used by another system, rather than designed to be directly viewed by a human. 

A RESTful API is an application program interface (API) that uses HTTP verbs/standard methods to `GET, PUT, PATCH, POST, and DELETE` data. This architectural style is used by most sites on the web, not limited to Youtube, Facebook, Amazon, and LinkedIn. In communicating information from the user to cloud services, a RESTful API follows strict guidelines that govern how to transfer and access data behind the scenes from the user. APIs are used for ads, games, user account data, payments, communications, and sharing stats. 

Currently, working in Rails, I have used RESTful principles in all of my codework to date in both the MVC and API context. Rails is a web application framework written in the Ruby language that capitalizes on RESTful principles for ease of workflow and standardization across systems. In the Model-View-Controller (MVC) context, communication cycles between client and server using standard requests and messages that map paths from controllers to actions. HTTP verbs (GET, POST, PATCH, PUT, DELETE, etc.), match to a cooresponding route and the server, in turn issues a response to controllers which then render a view. View templates use html and/or erb (embedded Ruby) to format the HTML response and viewable page the controllers initiated, to the web server. This table shows the HTTP verb, path and corresponding actions for CRUD (create, read, update, and delete) operations.

![](/img/Table.png)

The GET `/documents` action shows all documents, whereas the POST `/documents` action creates a new document. The GET `documents/new` action renders the form for creating a new document. `:id` in this context, corresponds to the individual identifier for 1 document. Using the paths and controller actions in the above table `/documents/:id` paths can render the form for creating a new document, show a single document, update a document and delete a document when associated with the associated HTTP verbs. This format is standard Rails using MVC, where views, models and controllers are within the same application and logically connected. 

APIs are the hidden portion of a computer that make website data more accessible to a computer to view and edit. APIs use clients outside of your application, such as another server or a mobile phone application to make a request to your server to obtain or modify data. Controllers then respond to requests with formats such as JSON or XML. 
API routes use RESTful principles and use HTTP verbs (some of which, are listed in the above table) to send and receive data when linked to a specific URL. However, that is just one potential aspect of RESTful design. 

RESTful design principles, including the following topics, will be elaborated on in a later blog post:

* Client-server architecture
* Resource naming
* Unique Identifier (URI)
* Stateless request model
* Cacheability
* Layered System
* Code on demand
* Uniform Interface
* Representation for all communication (XML, JSON)
* Building a layered system to increase scalability 
