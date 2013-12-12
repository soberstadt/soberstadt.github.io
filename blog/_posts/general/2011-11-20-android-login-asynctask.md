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

{% gist soberstadt/d92305d0cac5fdca497d %}

### Step 2: LoginActivity.java

Every Android developer knows Activities but one thing important here is are the last two methods which are called by the AsyncTask to change the UI.

{% gist soberstadt/a4e2dd7c6857a562d98a %}

### Step 3: LoginTask.java

Here we have a class that extends the AsyncTask class which will run behind the scenes and talk to the server while you keep your user engaged with a cool progress bar/wheel. The important parameter “activity” of type LoginActivity allows you to call its methods login and showLoginError.

{% gist soberstadt/f70154c6f56a72ae97dc %}

   [1]: http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html
   [2]: http://developer.android.com/reference/android/os/AsyncTask.html
