---
layout: post
title:  "Force Refreshing Chrome Favicon DB from Mac Terminal"
date:   2018-3-12 16:16:01 -0600
categories: Web Development
---

_March 19, 2018_



Google Chrome caches the favicons of sites that have been browsed by the user. Once they are cached, 
they stay there until the Favicons DB is removed. Generally that works perfectly, since favicons are hardly 
replaced. However, sometimes you want to see the latest favicons. Especailly when you are developing 
a web application that has a favicon. Then you can do one of two things:
1. Completely remove the Favicons DB
2. Remove the specific favicon from the Favicons DB

In both cases, Chrome will be forced to download the latest favicon during your next visit.

You can do that by following these steps:

<strong>Step 1: Close Chrome</strong>

<strong>Step 2: Go to the directory where the Favicons DB lives</strong>

If Mac OS X:
`~/Library/Application Support/Google/Chrome/Default`

If Linux:
`~/.config/google-chrome/Default`

If Windows:
`C:\Users\%USERNAME%\AppData\Local\Google\Chrome\User Data\Default`

<strong>Step 3: Remove the file</strong>

Just delete `Favicons` or to delete a spcific favicon do the following:
1. Load the favicons database:
   `$ sqlite3 Favicons`
2. Search for the favicon:
   `> SELECT * FROM favicons WHERE url = 'http://mysite.com/favicon.ico';`
3. Delete it:
   `> DELETE FROM favicons WHERE url = 'http://mysite.com/favicon.ico';`
4. You can also search for a pattern that you can reuse to delete multiple entries:  
   `> SELECT * FROM favicons WHERE url LIKE 'http://mysite.com%';`  
   To delete all the results of the output:  
   `> DELETE FROM favicons WHERE url LIKE 'http://mysite.com%';`  
5. Exit the database:
    `$ .exit`

<strong>Step 4: Restart Chrome</strong>

You should see the latest favicon now in Chrome.

<br>


    
    
