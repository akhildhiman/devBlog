---
title: 'How The Web Works'
date: '2020-03-19'
category: 'General'
---

![](https://mdn.mozillademos.org/files/8973/Client-server.jpg)

<br>

We've come to a time where internet is omnipresent and browsers play an important part when it comes to communication between the client and the server. Wait, hold on! 

Client is usually the computer or a machine that a user has access to, and wants to access some resource from the server. Server is not an imaginary cloud of information, it's also someone's computer located elsewhere or your local machine if you've created and set the server yourself for your web app. For example, Piratebay has many servers located at different locations(that no one knows).

In this article, we'll go through the process of how you get to see what you see, i.e., **information(web pages)** in your browser and all that's happening behind the scenes within a fraction of time.

Let's say you're using Google Chrome and want to go to Google's home page. Well, you'd just type the URL in the address bar, hit enter, and get the page. As simple as that. Now, let's look into some more details what the web has to offer.

When you search for an address like `google.com`, the browser doesn't really remember the websites by their URL. What browsers are really interested in are the IP addresses of the websites. So, in order to fulfill your request, there's something called DNS lookup. But first we ought to know what DNS really is.

<br>

# Domain Name Systems

**DNS** is the phone book of the internet, but with **a list of URLs and their IP addresses**. Just like we look for the person's name and then his associated phone number in the phone book, similarly, DNS servers have the URLs of websites and their IP. Interestingly, you could easily access the website just by typing in the IP address in your browser's address bar. In case you're really wondering, you should check this tool called [IPChecker](https://ipinfo.info/html/ip_checker.php).

We can access `www.google.com` by its IP address- _172.217.9.238_. We need not to remember the IP everytime we're requesting for a webpage. That's where DNS comes in. All in all, DNS links and stores host names(www.google.com) to a specific IP address. These records are known as DNS records.


![](https://www.seobility.net/en/wiki/images/d/d0/DNS-Server.png)


Every URL has a unique IP address associated to it. So, the aim of the browser is to look in the DNS records, the IP address of the server where the website lives on.

Before we dive further in, you should know how the client and the server communcicate with each other. I like this analogy from the docs and it says- **For now, let's imagine that the web is a road. On one end of the road is the client, which is like your house. On the other end of the road is the server, which is a shop you want to buy something from.**

Let's imagine this with The Beatles emerging from their house crossing the Abbey Road and going towards the shop for buying some classic vinyls.

![](https://www.udiscovermusic.com/wp-content/uploads/2017/09/The-Beatles-Abbey-Road-Album-cover-web-optimised-820-820x600.jpg)


Client machine is connected to the internet via its **Internet Service Provider** like Verizon, AT&T etc. ISPs have their own DNS servers.

> Every ISP has a database of DNS names and their corresponding IP addresses.

<br><br>

## The Flow

* Your Browser makes a request to `google.com`.
* Your ISP will look for the IP address of the server that hosts `google.com`. 
* If It finds out successfully, the communcication channel is opened with the server that matches the IP address, a.k.a **TCP/IP**.

<br>

> **TCP/IP** is the fancy name of the networking protocols or a set of rules designed for how the data should travel across the web. **HTTP** requests are made over this protocol. Data is sent via packets or small chunks for they are convenient when a large number of users are accessing the same website. Sending data via a single big chunk would be okay for a single user but horrendous for multiple users.

<br><br><br>

Request usually contains the information like the client's info, desired address, browser name, request method, connection-headers, cookies(to identify the user) and the response will mostly be status codes, the actual data, etc.

<br>

![](https://mdn.mozillademos.org/files/13821/HTTP_Request_Headers2.png)

<br><br>

* After the connection is established, browser sends a **GET** request asking for `google.com` and  google's server sends the response to the browser. Browser downloads the HTML, CSS and the JS, the three things responsible for a web page to show. Finally, you can access Google's home page. Hooray!


<br><br>

---
Thank You for reading this article. Follow me on [Twitter](https://twitter.com/_himalayan_) for more updates.



