---
layout: post
title:      "Scraping and Clawing"
date:       2020-06-28 22:18:56 +0000
permalink:  scraping_and_clawing
---


After coming to the same hopeful conclusion "This has to be the hardest part", every few days, I was finally able to look with hindsight and determine that the task of looking over the Nokogiri object that was created whenever I parsed the HTML from my get request was esily the hardest thing that I had to endure.

It seemed that the entire time I was working, I had to constantly change paths due to the continual learning that takes place when inspecting a webpage that you are scraping.  It started off with identifying how to access sport-specific ESPN pages.  That wasn't so hard because accessing the page is simply adding the "/sport" to the end of the ESPN.com URL.  Then the REAL fun began.

The next step in my process was to inspect the page using the inspection tool so graciously provided by Google Chrome.  What followed was anything but graceful.  It was easy to locate the TOP HEADLINES section of the page.  That was located in a simple class of 'div.headlineStack'.  That much I knew.  But what I wasn't entirely sure of was how I was going to access the information INSIDE of this class.  

I quickly refreshed my memory on how to go 'deeper' into something I was scraping. So I thought if I just added 'section ul' to the class I found when I was inspecting, I would easily be able to take all the information I needed and this project would be complete before I knew it!!  Not. Even. Close

Sure, it was a simple hash filled with hashes of arrays.  I'm no genius *yet* but I felt resonably confident I could manage my way through that iteration witih an .each_with_index method.  Then, because scraping just can't ever be simple, I hit a snag.  One of the most important pieces of information (the title of the article) was not accessible in this location due to it being javascript.  =(  So then it was time to think...

I was lucky enough to learn pretty quickly how to access the article of the page just by going to the article and looking at how the URL changed from where I just was.  I saw that each article had an ID number that was inserted just like I had done previoiusly!  Another quick inspection and iteration, and BOOM, I've got my IDs.  After that I was on a roll.  I knew that since it was going to be a new webpage I had to use HTTParty, Nokogiri, and of course open-uri.   I would then just take the URL and add what I found and I'd have the access to any article I could want!  

Wash. Rinse. Dry. Repeat.  I inspected multiple article pages to make sure that ESPN kept a consistent formatting for each page and, once I confirmed they did, taking the title information and setting it to an instance variable within my scraper class wasn't so bad. I say that like it didn't take me the majority of a week to figure it all out.  BUT I did it.  
I went on to tie the IDs to the title of the article that they represented for an easy work flow after that.




