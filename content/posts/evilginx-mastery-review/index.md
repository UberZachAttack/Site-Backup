---
title: "Evilginx Mastery Review"
date: 2023-12-03T23:31:09-05:00
showSummary: true
summary: "Quick review of Evilginx Mastery course and helpful tips to use while taking the course."
tags: ['Review']
---

![Article picture](feature.png)

While pursuing the interwebs, I stumbled across this video from [John Hammond](https://youtu.be/sZ22YulJwao?si=hv8CE5n33rsCX9Qq).

{{< youtube sZ22YulJwao >}}

Since I had professional experience with Evilginx and plan to use it more in the future, I took advantage of the discount and decided to buy the course.

Even though I have worked with the tool before, I knew I had limited knowledge with using it and could not use Evilginx's capabilities to the fullest. The course was very well done and straight to the point. The training labs provided were extremely helpful in cementing how to use the functions and features provided in Evilginx.

The course is broken down into 7 sections: Intro, Setup, Getting Started, Advanced Phishing, Security Hardening, Remote Deployment, Deep Sea Phishing. I will be briefly describing what these sections are and what they cover in a little bit more detail than was is provided from the [BREAKDEV Academy site](https://academy.breakdev.org/).
### Course Overview
#### Intro
Kuba talks about the history of phishing and how reverse proxy phishing arose and become the main standard for phishing attacks today. This is mainly due the addition of multi-factor authentication so attackers had to account for session tokens as well as credentials when phishing. He then explains how Evilginx works from a high-level perspective. 
#### Setup
There is a basic walkthrough of how to setup your environment for Evilginx and what tools to run. Kuba goes through the setup of a Windows environment but it is pretty much the same for Linux. The setup is:
- Install Visual Studio Code 
- Install and  setup Chrome with profiles
	- Adding the necessary extensions for editing cookies and local storage
	- Making the delete history setting accessible for testing purposes
- Installing Go + Git + Evilginx

Once this is done, Kuba goes over the training labs that are already setup and ready to use for the students. As of currently, there are 4 labs available. Whenever you first purchase the course, you will receive your account information such as the username and password to use. Once you log into the lab environment for the first time, you will be prompted to add MFA. 
#### Getting Started
This is where the fun begins. However there is some extra setup requirements needed, especially if you are on Linux (mostly Ubuntu from what I have seen).

First, you need to build Evilginx first. If on Windows, you run `build_run.bat` / `build.bat` or use the `make` command on Linux. For Windows users, you can keep using `build_run.bat`. The script will automatically rebuild the binary and run it using the necessary flags for developing phishlets for the course. All of this is already described within the [documentation](https://help.evilginx.com/docs/getting-started/building).

As for Linux users, once the binary is built you can run Evilginx as so:
```
sudo ./build/evilginx -p ./phishlets -t ./redirectors -debug -developer
```
This is essentially the same command that is ran within the `build.bat` script.

Once that is complete, Kuba goes over the first lab provided and covers what the general process is for creating a phishlet. Then using the credentials you have for the lab, you phish yourself, and then successfully impersonate your own account!
#### Advanced Phishing
This section is entirely about how to utilize different features within Evilginx. It covers
- Content replacement and changing the way the page is presented to the user
- How to force POST parameters like the "Remember Me" button parameter
- Looking for JSON cookies and local storage
- JavaScript injection to add custom JavaScript code to your phishing page
- Landing page redirectors, essentially having a landing page before the phishing login page is presented
- Mass lure targeting in which you can import emails and names of targets and produce a unique link for each target. Most useful in combination with redirectors and using custom parameters
- Proxying the reverse proxy. Or in other words, setting up Evilginx to send all its traffic through a web proxy like Burp Suite for more analysis / debugging
- Blacklist management and the various blacklist modes that can be used and the reasons for why they would be used
#### Security Hardening
Different security measures are covered and shown in the last 2 available labs. These being location validation and secret token validation. Kuba shows what the security measures would look like against a basic phishlet, how to look for the security protections in place, and how bypass them.
#### Remote Deployment
Kuba covers how to properly setup Evilginx remotely for real phishing engagements. This goes over the entire process of creating a remote server / VPS, setting that server up with the proper permissions and access, getting a domain hostname, installing Evilginx and setting it up for remote deployment such as having a blacklist, and how to keep persistence with Tmux
#### Deep Sea Phishing
The final section covers Kuba's process of creating a phishlet on real login pages. These include Okta and Microsoft 365 Personal / Entreprise account logins. 

### Tips and Tricks
Now, for things to look out for when taking the course.

I highly suggest and recommend that anyone that takes this course thoroughly looks through the comments of the videos. There are only a couple videos that should be looked over for comments since they contain information that could help you and or give more clarity to what is seen in the video. Below are the video titles to pay attention to and why the comments should be looked at.
- Preparing the Enviroment
	- At the time of the recording, Kuba was using an extension called LocalStorage. That extension got flagged for malware so it is recommended that students use StorageAce. This was later addressed when the Microsoft 365 Personal / Entreprise sections were added.
- Catching a Phish
	- If you are on Linux, you most likely had an issue with importing the CA certificate. There are multiple comments on how to fix this issue and I will show my methods of fixing this issue later on below.
	- There was another comment made on how the cookie was captured without the ":always" modifier added. This is due to the 3.2.0 version of Evilginx always captures session-cookies even without an expiration date. In the video Kuba was using version 3.0.0.
- JavaScript Injection
	- At the time of the recording, Kuba was using Evilginx 3.0.0. When doing JavaScript injection, the injected code would appear at the bottom of the page source. However, with version 3.2.0 the JavaScript injection is loaded in a separate JS file. 
- Deploy Evilginx
	- If you are having issues with DNS (which there always are), then reading the comments will definitely help. It appears to be a issue when using Evilginx on Ubuntu Linux but it might be similar on other distros as well. I will also give tips for how to fix any DNS issues below. Fixing DNS issues for Ubuntu has led me to the point of me considering buying this shirt due to how many times I had to deal with it.
![DNS Shirt](https://images3.teeshirtpalace.com/images/productImages/iad6982331-its-always-dns--black-at-garment.webp?width=700)

#### CA Certificate Import
For Linux users, depending on how you run Evilginx, you will have to check two places for the CA certificate to import directly into Chrome to fix the issue of the 'connection is not private' message when visiting the local phishing page.

First, if you are running Evilginx **without** `sudo`, then you can use the certificate found in your home folder under `.evilginx/certificates/ca.crt`

If you are running Evilginx **with** `sudo`, then you have to import the certificate found within root's folder. However, you have to change the ownership of the certificate before you import it into Chrome. The commands in order should look something like this:
```
sudo cp /root/.evilginx/crt/ca.crt <Directory of your choice>/evilginx.crt
sudo chown <Your username> <Directory of your choice>/evilginx.crt
```
Once the ownership is changed, the certificate that was copied from root's folder should be able to be imported and the phishlets for the training labs should be able to load properly.
#### Linux DNS Fix
As for fixing DNS within Linux, one of the comments recommended running these commands if you are running Evilginx on Ubuntu.
```
Edit the file: /etc/systemd/resolved.conf
- Add "DNSStubListener=no"  
Then restart service: sudo systemctl restart systemd-resolved
```
Another method that I use is to do the following:
```
sudo systemctl stop systemd-resolved.service
Remove symlink: rm /etc/resolv.conf
Recreate the file: vim resolv.conf
Add: "nameserver 1.1.1.1 <new line> nameserver 1.0.0.1"
Check DNS with nslookup: nslookup google.com
Permanently change it: vim /etc/NetworkManager/NetworkManager.conf
- Within main, input "dns=default"
```
This should fix the issue of Evilginx not being about to establish a nameserver when starting up.
### Conclusion
Overall, it is a great course. I would recommend this to anyone that wants to enhance their red team capabilities specifically for phishing and or wants to learn more about Evilginx. There were a couple times where the videos do not match up with the current version of Evilginx but that is expected with a video-based course.

I would like to end this article with a comment made by someone at the start of the Deep Sea Phishing section:

*"Give a man a phishlet, he'll phish for a day. Teach a man how to create a phishlet, he'll phish for a lifetime"*
