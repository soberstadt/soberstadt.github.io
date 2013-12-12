---
title: Asynctask in Android and onCompleteListener
author: Spencer
layout: post
permalink: /asynctask-in-android-and-oncompletelistener/
categories:
  - General
tags:
  - Android
  - AsyncTask
  - Event Listener
  - example
  - HTTP Request
  - Java
  - onCompleteListener
---
From time to time you only need to do a simple HTTP request for various reasons(login, vote submitting, simple server requests, ect) in a Android project. A lot of times this can be over complicated by writing a AsyncTask for every different type of request, but I have a simple class here that should help you understand AsyncTasks in Java as well as save some time.

Below you will see two files, GeneralHTTPRequestExampleActivity.java and GeneralHttpTask.java. The first is the implementation and the second is the class that we are using.

In the AsyncTask, you will see a few interesting things. First, that it extends AsyncTask and includes methods to do the basic execution of a AsyncTask where it shows the ProgressDialog, executes the request, then dismisses the ProgressDialog. Second, you will see the OnResponseListener interface. This is how we build a logical link between the threads. The constructor of GeneralHttpRequest accepts a OnResponseListener object that is written in the Activity. Third, a ProgressDialog class, which is a pretty basic extension that makes a typical ProgressDialog.

{% gist 1679019 %}

Note: your app will require the INTERNET permission in the manifest. See [my manifest][1].

Pull the example project on my [Github Repo][2].

   [1]: https://github.com/soberstadt/GeneralHttpAndroidExample/blob/master/AndroidManifest.xml
   [2]: https://github.com/soberstadt/GeneralHttpAndroidExample (General Http Android Example)
