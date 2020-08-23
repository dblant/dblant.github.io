---
layout: post
title:      "MyLibrary Sinatra Project and Learning How to Read Carefully"
date:       2020-08-23 23:53:27 +0000
permalink:  mylibrary_sinatra_project_and_learning_how_to_read_carefully
---


This project, in an of itself, is very straight forward.  The goal here was to simply create a Sinatra application that utilized multiple models(User and Book) and followed some simple parameters. 

The base functionality is that a User can Sign Up / Log In and that User is then persisted into the database.  After the User is successfully created, they are then given the option to "Add a Book". Not too complex, it was a simple form with a Post to a route that would know to create a new instance of my Book class with the data the User had entered(Title, Author, and Genre).  That Book would then be given a "user_id" that would tie it to the specific User.  Once the book is created, the User would then be redirected to their User specific homepage where it would display the books they had added. Furthermore, to satisfy the requirements, there are options to edit each book that was being displayed, or delete one altogether.

It's easy now to explain it, but the road to the final product was arduous to say the least. I enjoy discussing the functionality of the program, but the problems that I encountered seem to be more of a prologue.  I believe it helps add context into how this program came to be and really what the process represented.  In this instance, I learned a lot more about "sessions" and by virtue of the many files that comprise this project, I acquired a deeper understanding of exactly what purpose each element within those files serves.

To trim the fat, so to speak, of this story I will tell you that I narrowed my issue down to my Session hash that was created when I enabled Sessions in the config at the top of my ApplicationController class.  Particularly, the "session_id".  

The problem therein was that when a User creates a book, they are entering their data into a form and sending it off, as mentioned above.  That route they it was sent to takes the Title, Author, and Genre (params) and uses the "current_user.books.create" method to then create a new Book for the User to store and display. In theory, it should be working.  In practice, it produced the terrifying Unidentified Method for nil:NilClass, and down into the rabbit hole we go.  
A quick binding.pry proved to be extremely useful as I used it in almost every route I created.  I wasn't sure where I was going wrong, until I noticed somethinf was off.  While using the pry inside the terminal, I entered "session" to gain a visual to the entire Session hash.  It's really just a hash with a bunch of jumbled up characters that were assigned to keys, one of which was "session_id".  

Now, if you are unfamiliar with how sessions work, I totally suggest reading the lesson within Flatiron's curriculum.  To be brief, it is what allows data created on one page of the web to be persisted to the next page.   It does this, in part, because the jumbled up letters that make up that "session_id" are the same from one page to the next.  At least, they are supposed to be.

When I placed another pry into the next stop that the User entered data would be making, so to speak, I found that the session_id was not the same as the previous place I had checked.  This was confusing, but informative(and such is the plight of one who codes).

What this told me was that my session was not working, but what I couldn't figure out was why. I searched each and every folder and file in my program to try to understand.  Sessions was already something that I wasn't super clear on.  On the surface I knew what they were meant to do, but now that it was in practice my mind raced and I knew I just had to start somewhere in looking for answers.  This is what brought me closer to the purpose of each of the individual innerworkings of my code.  I went through each item and researched what it's purpose was just to make sure that it wasn't possibly tied to the reason my code wasn't working.

*SIDE BAR:  Making mistakes is easily the most frustrating and rewarding thing I do when programming.  It REALLY forces me to take a step back and ask myself if I really understand what I have created.  Anyway, back to your regularly scheduled programming(pun intended).*

It wasn't until after 6 hours had passed that I had decided to try the old Occam's Razor approach.  I would check the simplest place first, because for whatever reason I assume that if there's a problem it must then be complex.  I looked at how I had set up my Sessions and compared it to a friend would was very generous in providing me with an example of working code.  

I combed and continued to look.  It all seemed to be correct, and that was maddening.  It wasn't until I started to wonder if I had made the most trivial mistake. 

A typo.

Looking back over my configuration of Sessions, I noticed that I had made the error of setting a "sessions_secret" instead of a singular "session_secret".  One click and tap of the backspace key and my problems were solved.  I wanted to cry, but instead I laughed. I grew my knowledge of my entire application's structure vastly, and I have the letter "S" to thank for it.  





