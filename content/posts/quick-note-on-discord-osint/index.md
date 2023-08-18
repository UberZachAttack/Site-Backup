---
title: "Quick Note on Discord OSINT"
date: 2023-08-18T13:41:01-04:00
showSummary: true
summary: "I will be going over Discord OSINT techniques and methodologies that I have not seen online."
tags: ['Research']
---
![Article picture](feature.png)

I wanted to write about Discord OSINT techniques since there were a few that I have used that I haven't seen mentioned anywhere online. The only article that brings up most of what I will be writing about is this one from [OSINTCurio.us](https://www.osintcurio.us/2021/05/06/investigating-discord-a-primer/). The article does an excellent job of covering techniques that can be used when gathering OSINT within Discord. Some other resources that I found on the subject are a couple of GitHub pages. The first one is  [OSINT-Discord-resources](https://github.com/Dutchosintguy/OSINT-Discord-resources) and the other one is [DiscordOSINT](https://github.com/AtonceInventions/DiscordOSINT), but it is very limiting. Most of the techniques online are useful but they don't really cover other techniques and methods that could be used to in conjunction with gathering information on a person of interest.

However, it should be noted that Discord is not the best for OSINT. Information within Discord is not very 'open' since it requires user authentication and invite links to public / private servers and or chat rooms. Though OSINT techniques can still be applied to people of interest which I will cover shortly. Also, I will be talking about these methods assuming that you already have a general understanding of OSINT.
### Basics

Most of what is online covers how to use the search function (found within the top right) within Discord. This is just as powerful as Google dorking. Searching for `from: uberzachattack` would bring up everything that I have said within the Discord server you are viewing. Adding other terms and keywords such as `has:` or `in:` can narrow down where you are looking and what you are looking for.

Chaining everything together would provide something like `from: uberzachattack has: link in: server-invites`. This would hypothetically search for any instance where I might have shared a Discord server link within the channel `#server-invites`. Keywords can be used as well without any operators. You can even search for the keyword `discord.gg` as mentioned in the [OSINTCurio.us](https://www.osintcurio.us/2021/05/06/investigating-discord-a-primer/) article.

Here is an example search of searching for links within general chat, the search being `from: uberzachattack has: link in: general-talk`
![Test](https://i.imgur.com/ISW1qbj.png)

This is a common method brought up online regarding Discord. It all comes back to trying to gather as much information from a person of interest and seeing if they have sent any messages that would be of interest to us, such as private Discord server invites or PII. 

Another method that I found is basic searches for public Discord servers. One site that comes to mind is [Discordbee](https://discordbee.com/). This can certainly help, but you can search for servers within Discord with the Explore function or even through a simple Google search.
### 1. Linked Accounts

This is brought up online a few times, but it is something worth mentioning. A lot of people on Discord are unaware of the fact that they exposed their accounts to other services including personal ones. This is controlled within the user settings within the `Connections` tab. The accounts that are linked can be hidden from your profile.

Seeing what linked accounts there are can help with identifying any personal accounts like Facebook or Instagram or even help discover a different username or alias that is used by the person in question.

The first example is something more commonly found, there are a couple of linked accounts but the person in question did not realize that they linked their real name to their Discord username and usernames with other services listed.
![Example 1 with Linked Accounts](https://i.imgur.com/WEqjXHw.png)

The second example is of someone that does not realize how much information they are sharing through their connected accounts. You can link 4 usernames and a real name to all the accounts that are shared, with 3 of the connected accounts having the person's real name.
![Example 2 with Linked Accounts](https://i.imgur.com/pw7A7U1.png)
![Example 2 part 2 with Linked Accounts](https://i.imgur.com/mBnbRiG.png)

As you can see, you can tie a real name to an alias that the person of interest uses.
### 2. Mutual Servers

This is something that I have done plenty of times to see what other servers people might be a part of.

This will be covered more in depth later on, but the main thing is that this can give you an idea of what the person is interested in based on what servers you and the person of interest are both within. The mutual servers found can things like gaming servers, coding communities, or cybersecurity servers.

Also, Discord users are able to set different nicknames for themselves in different servers. This could also reveal different usernames and aliases that the person of interest might use. This would lead us back to `Linked Accounts`. 

Here is an example of a user having different nicknames / usernames in different servers:
![Example with mutual servers](https://i.imgur.com/PwU7RDq.png)
### 3. Student Hubs

One of the biggest places to gather OSINT within Discord that is not mentioned online at all. The only stipulation is that you need to have an `.edu` email at a certain University in order to join Student Hubs. The one I will be covering is the PSU Student Hub. 

The biggest mistake people make is using their full name when joining a Student Hub. The prompt asks for your name whenever you join, which people put in, unaware that it will appear on their Discord profile through mutual servers.

![Student Hub Mutual Server](https://i.imgur.com/rGnhJ8F.png)

Another important note, Student Hubs do not have any moderation oversights at all. You can report servers within the Student Hub but that is about it. The only moderation that is used is that you have to verify your `.edu` email when you try to join a Student Hub. After that, you are free to link a Discord server that you run or moderate to the student hub and join whatever Discord servers are listed within the hub. I am still able to access the student hub for PSU even though I have graduated over a year ago.

![Student Hub](https://i.imgur.com/rBev1PU.png)

You could try to look for public University Discord servers through Google but Student Hubs give you direct access. However, there are a couple instances where there will be unrelated Discord servers that are within the PSU Student Hub that do not have any affiliation to PSU at all. The only way that they would be added to the Student Hub is if a server admin or moderator of the server added it themselves, in which you would know that it was a student / faculty member (Mainly students since Discord is for zoomers).
### 4. Fingerprinting Community Types

This is the most intensive process when it comes to the techniques and methods that I have discovered for Discord OSINT and the main technique that I wanted to talk about.

I will show examples of fingerprinting the Cybersecurity Discord communities and how to fingerprint a University's Discord communities through Student Hubs. I'll start with cybersecurity since it is more applicable and accessible (and one that I am involved in the most).

If we are in a situation where we are gathering information on a person of interest through Discord, the most important element is to try and identify what communities they are involved in. In this hypothetical case, the person of interest is heavily involved within the cybersecurity community. With that in mind, we should try and find what the biggest Discord servers are that are related to cybersecurity. Some that comes to mind are [DEFCON](https://defcon.org/), [HackTheBox](https://hackthebox.com/), [TryHackMe](https://tryhackme.com/), [TCM Security](https://tcm-sec.com/), etc. Other servers that could be on the list would be online personalities like [John Hammond](https://www.youtube.com/@_JohnHammond), tool developers (Hashcat or [Porchetta Industries](https://github.com/Porchetta-Industries)), or even cybersecurity companies (Like TCM or even [Red Siege](https://redsiege.com/)). 

Now that we have a small collection of servers, we can try to see how much involvement they have within each server and the Discord server community at large. 

Based on the amount of servers the person is within, we can gauge their level of involvement. Here are some examples of what the person's involvement might be. We could also make assumptions about what type of person they are based on the Discord server's ethos, personalities, and culture.

The methodology here is simple, join as many servers as possible that pertain to the community.

Initially, our server list that we are a part of would look like this:
![Initial Visibility](https://i.imgur.com/Hr46Yvw.jpg)
Servers:
- DEFCON
- TCM Security, HackTheBox, and TryHackMe have not been joined yet

Once we join some servers that are within the cybersecurity community, the visibility of what servers the person of interest is in would be shown:
![Improved Visibility](https://i.imgur.com/cXIHkJS.jpg)
Servers that we have joined:
- DEFCON, TCM Security, HackTheBox, TryHackMe, Zero-point Security, Blue Team Labs Online, Security Blue Team, Hashcat, Red Siege, Black Lantern Security, PicoCTF, Porchetta Industries

To further illustrate what I am demonstrating, below are some sample profiles that will be used as case studies.

#### Case Study #1
List of mutual servers:
![Case Study 1 Mutual Servers](https://i.imgur.com/bRYTP7V.png)

Server Visibility Representation:
![Case Study 1 server representation](https://i.imgur.com/3VvEWj5.png)

For case study #1, there is a heavy emphasis on training companies. TCM Security, HackTheBox, and TryHackMe provide platforms for training and practicing your cybersecurity skills.
#### Case Study #2
List of mutual servers:
![Case Study 2 Mutual Servers](https://i.imgur.com/SHQS0Wc.png)

Server Visibility Representation:
![Case Study 2 server representation](https://i.imgur.com/xHonieu.png)

For case study #2, we can infer that they have an interest within offensive security and studying for it. This is due to TCM Security, HackTheBox, and Zero-point security providing training and having certifications like the PNPT, CPTS, and CRTO respectfully.
#### Case Study #3
List of mutual servers:
![Case Study 3 Mutual Servers](https://i.imgur.com/Q4IPwc6.png)
![Case Study 3 Mutual Servers 2](https://i.imgur.com/WHxzPID.png)

Server Visibility Representation:
![Case Study 3 server representation](https://i.imgur.com/T1Pw6lX.png)

For case study #3, we can infer the same information as case study #2. However, they are also a part of [Porchetta Industries](https://porchetta.industries/). They host a lot of popular, open source tools such [CrackMapExec](https://github.com/mpgn/CrackMapExec). Based on this, case study #3 might be interested in tool development. 
#### Case Study #4
List of mutual servers:
![Case Study 4 Mutual Servers](https://i.imgur.com/WQMl6xL.png)

Server Visibility Representation:
![Case Study 4 server representation](https://i.imgur.com/xxPEgzy.png)

For case study #4, they are the most unique compared to the other case studies. Based on what servers they are in, there is a heavy emphasis on defensive security. It is safe to say that this case study works as a SOC analyst and or is interested in learning about defensive security.

Then for Student Hubs, the work of trying of finding what servers are a part of the target community is removed and is easily given to us.
![Simple Diagram PSU](https://i.imgur.com/5jzkc0H.png)

Same methodology as before, join as many or specific (Computer Science, Cybersecurity, etc.) servers to gain more visibility.
![Better PSU Visibility](https://i.imgur.com/RQRke5W.png)

Then using the methods and techniques talked about earlier, we can try to see if they use different aliases or nicknames, looked at linked accounts, and most importantly search through their chat history to look for interesting information.

The mutual servers found on someone's profile can even give insights into what type of demographic and personality they might have as stated earlier.

### 5. Location Based Servers

Another interesting element of mutual servers are joining servers that can be tied to certain locations. 

Servers that come to mind are BSides Discord servers. If you have enough location based servers, such as BSides or DEFCON even (although it is a global level conference), you would be able to infer the location that the person of interest lives in.

Let's say you have server visibility on BSides Harrisburg, BSides Philly, and BSides Charm (Baltimore) and the person of interest is within those Discord servers, you could infer that they live within the area of the Southeast PA, Northern Maryland and Delaware, and Southern New Jersey. 

**NOTE: BSides Harrisburg is the only conference in this example with a Discord server, however this is a demonstration.**
![BSides](https://i.imgur.com/IfiaKkQ.png)

This should be analyzed carefully, if the event is popular enough then people would be willing to travel to them. I have gone to a couple of BSides events within New York and met a speaker that was from Chicago. If the Discord server is in a niche location, then there is a higher chance that the person of interest is within the same location area. 
### Conclusion

To summarize these techniques and methods with a high level overview, they are:
- Identify what communities the person of interest would be a part of
- Join as many servers that are within that community ecosystem to gain as much visibility as you can
- Once you have the person of interest's profile, looked for linked accounts and different nicknames within different servers
- Search for the person of interest's chat history within each server they are in to try and find interesting information about them
- Also join location based Discord servers that are within the community to try to find where the person of interest might live

One thing to keep in mind is that a Discord only allows you to[ join up to 100 servers, 200 if you subscribe to Nitro](https://support.discord.com/hc/en-us/articles/360034842871-How-do-I-join-a-server-). The best way to utilize these methods would be to develop a sock puppet account and have that tied to certain communities. There are many great resources and articles like [this one](https://garrettmickley.com/sockpuppet-account-creation/) that cover how to make a sock puppet account if you are interested in going that route. 

The only worry when utilizing these methods is that you will have to do manual verification as mentioned in the [OSINTCurio.us](https://www.osintcurio.us/2021/05/06/investigating-discord-a-primer/) article. Also, few servers might require active participation and prune any members that are not active within the server. The good news is that [logging into Discord every 7 days helps avoid this](https://support.discord.com/hc/en-us/articles/213507137-How-to-Prune). 

If you are interested in trying to protect yourself from these techniques and methods, here are a couple of tips:
- Review your connections within user settings
- The same old adage applies here in Discord, once it's on the internet it's there forever
- Keep your username the same for all servers
- To limit how many people join a private server of yours from trying to see if you posted any invite links, create invite links that expire or have limited uses

Now, use this information at your own discretion.

For those curious, [Toolscord](https://toolscord.com/) helped me with getting the logos for the Discord servers shown.
