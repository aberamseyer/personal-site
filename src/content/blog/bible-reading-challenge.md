---
title: 'Bible Reading Challenge System'
description: 'A system for a collaborative challenge to read more of the Bible.'
pubDate: 'Jan 2 2024'
heroImage: '/img/brc.png'
---
This is the most recent project I've worked on. My current work is with a Christian club at a local university. We encourage the students in the club to read the Bible more, and this system was developed to fill the need of collaboration and statistical tracking.

The system allows the staff members to create a reading schedule ahead of time using a calendar interface.

Then, as the days go by, the users access the website, the daily portion is displayed, and there's a big button that says "Done." Reading finished and button clicked, the system notes when and who's been keeping up. For our particular club, we incentivize the students who have read every portion for the current week, so the system tracks each reader's weekly progress.

![Schedule Creation](/img/brc-calendar.gif)

I owe the branding and the colorful badges to another team member with a design background, but the navigation and all other design was primarily done by me.

## Features

I had a lot of fun with this project. As someone splitting their time between development and the typical duties of the club staff member, I was very happy I could offer my skills to develop something used by everyone. This project's MVP took off in about a week of work, with further refinement and kinks being worked out with minimal time spent over the coming months. Today, I don't touch it, and it hums along perfectly.

1. Customizable reading schedules
2. Daily emails containing that day's portion to read–no website access needed besides clicking "Done"
3. Multiple Bible translations offered
4. Streak tracking
5. Badges
6. Individual and group statistics
7. Real-time page presence awareness of others

![Real-time updates](/img/brc-rt.gif)

We're all friends in the club here, and there's minimal user input on the site. Moderation thus was not a huge concern. The only user-generated fields are a reader's name and the emoji they pick to indicate their current reading presence.

## Tech Stack

1. Backend: php for the site, Nodejs for the real-time presence server.
2. Frontend: Plain Javascript. The site works fine without it, sans the real-time presence awareness
3. Database: SQLite (yes, it can handle concurrency!)
4. Email: Sendgrid
5. Real-time communication: websockets

By now you may realize that I love SQLite, mainly because it's already installed on every platform, as light weight as possible for a adatabase, and works without setting up a server.

![Statistics](/img/brc-statistics.gif)

I owe the branding and the colorful badges to another team member with a design background, but the navigation and all other design was primarily done by me.

## Regrets

None so far! I'm quite pleased with how this has turned out. I might look into a more plug-and-play solution for the real-time presence. I saw a couple posted on Hacker News recently, but can't recall their names. I might check one of those out if the link pops up again, but I think what I have in that area isn't too sophisticated beyond the boilerplate to begin with.
