---
layout: post
title: "This website"
date: 2019-01-19
excerpt: "How the sausage gets made"
tags: []
project: true
comments: false
---

Partly because I want to start filling up the "projects" list on this site, but mostly because I felt like I've learned a lot in creating this site, I'm going to explain exactly how this site was made. There are a few steps to creating a personal website, and I'll do my best to explain how I arrived at the decisions I made and what I did to make it work. This will be written from the perspective of someone who knows next to nothing about web development.

They are as follows: 
- Getting a domain name
- Choosing a hosting/building service for your site
- Using GitHub Pages and Jekyll to make a nice-looking site

## Domain names
You don't *have* to buy a domain name if you don't mind having a site that ends in .github.io. Personally, I wanted to have a website at my very own domain name.

There are many places to buy a domain name, and many types of domains! The most common is of course .com, and other familiar ones like .org or .net. There are also many country-code domains, some of which are extremely popular for [domain hacking](https://en.wikipedia.org/wiki/Domain_hack) and therefore much more expensive. If you have a name for your site that lends itself very well to such a trick, you should absolutely go for it. I went with a boring old .com domain.

However, keep in mind that not every service selling domain names supports all of them. I purchased mine through [Google Domains](domains.google.com), which was cheap but fairly limited in which kinds of domains you can buy. I got mine for $12 a year. Based on the reviews I read, it looks like Google is great for both price and simplicity. Many other services, like BlueHost or iPage, will bundle a "free domain name" with a website editor, but are much more expensive. More on that in...

## Hosting and building
Choosing between services for hosting and building your first website is like [trying to buy something from a Kumail Nanjiani character in a Portlandia sketch](https://www.youtube.com/watch?v=e4dcwCgv3ME). All of the options are roughly similar, but there are numerous hidden costs for things whose value you don't really know (do I need extra that extra security service? I don't know!). Although the prices as advertised seemed quite low for both BlueHost and iPage, I couldn't quite stomach the full cost when faced with the checkout pages (on the order of hundreds of dollars for multi-year plans). Sure, I'd love to have a what-you-see-if-what-you-get editor, but I also like to save money. So I decided to go with what a friend of mine did and use [Github Pages](https://pages.github.com/), which hosts your site for FREE and lets you build it for free as well. The only downside is that it requires a little more tinkering under the hood to get it that way. Which brings us to...

## Building a GitHub Pages site with Jekyll
The homepage of GitHub Pages is really nice. There's a friendly video showing you the basics of how to get set up, and even step-by-step instructions that allow you to get your site set up in minutes! I was feeling like a Real Hacker®. Even if you've never used git or GitHub before (and my own experience is fairly limited), it's very easy. 

However, then the tutorial ends, and there are links at the bottom of the page to further documentation on using Jekyll. Unfortunately, these are full of semi-redundant links to pages that link to other pages, creating a labyrinth of docs and leading the user to open far too many tabs than is good for their sanity. What to do?

### Keep calm and browse some themes
For the moment, don't worry about downloading Jekyll to your local machine. A good place to start is choosing a nice-looking Jekyll theme for your site. This will determine the general aesthetic of your site. There are a couple ways to do this:
1) You can use the Jekyll theme chooser on GitHub. By going into your repo settings, you can choose from a small number of themes. This is very easy, but you still have to customize it with your content. Additionally, your choices are very limited, so you might not find a theme that suits your needs. I decided not to go with this option.
2) You can use an open-source [Jekyll theme](http://jekyllthemes.org/), made by some friendly stranger! There are tons of themes on the site I linked to there, so you're bound to find something right for you. I went with the [Moon theme](https://github.com/TaylanTatli/Moon).

Many of the custom themes have instructions for how to customize them for your own use. Most involve just copying the repository into your own website and editing all of the relevant content and configuration files. There are also some instructions on GitHub for customizing your themes by overriding specific files, but this seems to require knowing how to use Jekyll and understanding which files to change. If you're a noob like me, it's probably best to just download the whole repository for your theme and edit files as needed.

### Using your custom URL
You can use the github.io domain name that is automatically generated, but you can also re-direct the site to your own domain name. This is fairly easy, but gave me some trouble when I was setting it up. 

As I understand it, you need your Domain Name System (DNS) provider and GitHub Pages to be pointing at each other. You might see somethings about how to set things up with your DNS provider in the documentation, but few specific details. I assume this is because different DNS providers have different methods of setting it up. If you went with Google, it's really easy!

All you have to do is go to the "DNS" page on the sidebar, scroll down to "Custom resource records," and fill it out like the picture below. Be sure to use the same IP address, which points to GitHub's servers. I had a problem with using an outdated IP address that I found on another blog post, so refer to the [troubleshooting page](https://help.github.com/articles/troubleshooting-custom-domains/) if there's an error with that.

![Domain setup](/assets/img/project_post/domain_setup.PNG "Easy peasy") 

Then, in the "Settings" under your GitHub repo, go to the section called "GitHub Pages". There should be a "Custom Domain" option, where you should put in something like www.elibpollock.com (which is my domain name). This should automatically create a file called CNAME in your main repo directory. If that's not there for whatever reason, you should create that file and put the domain name in there as well. In your options, be sure to also enable HTTPS, which is related to the level of security on your site. Otherwise, your browser won't trust your website and might try to block it!

### Editing your site
If you want to edit a bunch of files or add pictures on your local computer, you can do so and then use the following commands (assuming you've set up a git repo for your website and have a git-enabled command window open):
```
cd /path/to/website.github.io # Go to your repo
git add . # This tells git to "stage" all the files you've changed
git commit -m "insert message"  # Now you commit the changes to the local repo. The -m tag allows you to write a short message about what you changed in the commit.
git push origin master  # This adds your changes to the version hosted by GitHub. In a minute or two, your site should update!
```
You can also use the GitHub Desktop app if you have a fear of the command line. Or, you can directly edit the repo on GitHub! This is probably the easiest option for making blog posts.

### Customizing your theme
This obviously depends on the theme that you decided to use, but there are a few general points worth noting for people with no experience in web development:
- Be careful with the sizing of logo files or icon files. I had never heard of a favicon before working on this site, but it's the tiny little picture that appears in the tab when a browser goes to your website. This has to be saved to a .ico file, and the image needs to be a certain number of pixels. Pay attention to the default icon sizes, and make your own icons through a generator like https://www.favicon.cc/. 
- The config.yml file is going to be very important. Make sure you edit all of the relevant information there.
- Make sure you pick a theme that is well-documented and tells you how to customize it if you have no idea what you are doing. This may seem obvious but the lure of a cool theme can be strong.

### Local editing
It is possible to build your site on your local machine, and see changes at a localhost address without making the site go live. This is probably a very useful thing to be able to do, and if/when I figure it out I'll update this section. However, for now I don't have that workflow set up.

## Conclusions
I hope this post was useful to anyone who may have chanced across it. At the very least, it will serve to document some of what I learned in case I ever need to make another website.
