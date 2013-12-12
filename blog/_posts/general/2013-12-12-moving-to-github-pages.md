---
layout: post
title: Wordpress to Github Pages
tagline: Goodbye crappy GoDaddy hosting! Hello Github!
permalink: /wordpress-to-github-pages/
---

Last year when my GoDaddy hosting plan was up for renewal, I was't excited about spending $84 just so I could host my [portfolio][1] and a Wordpress Install that had a [few posts][2] that got maybe 400 hits a month. But was too lazy to move it anywhere. So I payed it and moved on.

This year, I wasn't about to give GoDaddy any more of my money they don't deserve (I'm still using them for my domain registrar).
### So I started moving to [Github Pages][3]. ###

## 1. Get your pages repo set up
First you're going to make a pages repo for your Github account, for me it was [soberstadt.github.io][4]. My site was originally setup with one static page (with assets of-course) and a blog. So if you're just hosting some static html pages and other stuff, you can dump them in the repo and move on. Otherwise, if you are looking for moving your blog over too, I would **really recommend** setting up [@plusjade][5]'s **jekyll-bootstrap**, follow his [quick start guild][6] to get started.

## 2. Export your Wordpress posts
I used fun plugin: [WordPress to Jekyll Exporter][7].  
After installing based on the README, and running `Export to Jekyll` from the tools, you're have a nice zip file with Markdown versions on your posts. Copy the contents of the _posts/ folder into a folder(s) inside the _post folders in your repo ([my example][8]).  

Now would be a good time to fire up a test version of your site by running `jekyll serve --watch` and visiting [localhost:4000][9], checking your Archive page for your posts.

## 3. [Set up your DNS record to point at Github Pages][10]
This was the intimidating part for me. But it actually isn't that hard. All you have to do is update your DNS record on your domain registrar to point at Github's IP address (204.232.175.78).

For GoDaddy:  
View Account > Domains > Launch on the domain you want to redirect from.

Then on the `DNS Zone File` tab, Click Edit, and change the '@' record to point to Github's IP address `204.232.175.78`.  
Like so:  
![11]

After that, simply create a new file in the root of the repository named `CNAME` with the only contents being the domain that will be directed to your page ([my example][12])

Don't forget to commit and push all your changes! Check my commit log for my progression.

## And you should be rolling
It may take a few hours for your DNS look-ups to update on your computer and others, but soon you should start seeing traffic to Gitub Pages via your domain.

## Advanced Tips
Things I did after this point:
*  Tweek my [theme][15]
*  Setup comments via [disqus][13]
*  [Setup Google Authorship recognition][14]

Let me know if you had issues with anything in the comments below.  
Keep hacking.

  [1]: http://www.256design.com/
  [2]: https://web.archive.org/web/20130723174148/http://256design.com/blog/
  [3]: http://pages.github.com/
  [4]: https://github.com/soberstadt/soberstadt.github.io
  [5]: https://twitter.com/plusjade
  [6]: http://jekyllbootstrap.com/usage/jekyll-quick-start.html
  [7]: https://github.com/benbalter/wordpress-to-jekyll-exporter
  [8]: https://github.com/soberstadt/soberstadt.github.io/tree/master/blog/_posts
  [9]: http://localhost:4000
  [10]: https://help.github.com/articles/setting-up-a-custom-domain-with-pages
  [11]: /blog/wp-content/uploads/2013-12-12-00-35-29.png
  [12]: https://github.com/soberstadt/soberstadt.github.io/tree/master/CNAME
  [13]: http://disqus.com/
  [14]: https://plus.google.com/authorship
  [15]: http://themes.jekyllbootstrap.com/