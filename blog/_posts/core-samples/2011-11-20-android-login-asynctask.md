---
title: 'AsyncTask Android Login with HTTP Post, &#038; PHP'
author: Spencer
layout: post
permalink: /android-login-asynctask/
categories:
  - General
tags:
  - Android
  - AsyncTask
  - httppost
  - Java
  - Login
  - MySQL
  - PHP
---
I am starting to work more with AsyncTasks and realizing that they are used for almost everything. However, I just started doing Android development, so I am by no means a master. Last night I realized that I was doing my login(and all http traffic) wrong by doing in on the UI thread. After researching for a while I finally figured it out. So Im putting together what I found so you can find this and quickly do it now.

Side note: Im using HTTP headers to speed up my response times, so instead of sending extra text like “success”, it taps into the already sent header code. [Read more about header codes and their definitions][1].

You might ask: “Why use an AsyncTask?” The big difference is for the user. When you call a HttpClient.execute() call, it freezes the call stack (think about how you can’t interact with a web page until it loads) and with it the UI. With an [AsyncTask][2] you execute long processes in a thread, which allows you update your UI in the middle of the call.

### Step 1: PHP

This is where you are going to have to change things. This php file is set up to access a MySQL table and check if the user email and password match those inside the DB.


1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69


