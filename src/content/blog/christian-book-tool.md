---
title: 'Christian Book Reading'
description: 'A system for reading and searching digital Christian books.'
pubDate: 'May 01 2023'
heroImage: '/img/books.png'
---
I love being a Christian. It's fundamentally the biggest part of my life, and for me, it's a wonderful experience to see more about who Jesus is through reading books that open up the text of the Bible to me.

To that end, I have a number of ebooks, but I wanted a digital way to read and parse these books. This application isn't too complex. Reading and searching takes care of my use cases for now.

I love the simplicity of building read-only applications. It makes things so much easier when you can trust all your queries, don't need to worry about bad data, and just give the user what you have instead of giving them back what they had in a different format.

## Features

1. Read the books
2. Search the books

However, my books were all in epub format, and a peak down below shows they are served out of a database. I think I used a javascript library to go through the 700+ books, read the epubs, and save the data into the database.

This application went through two phases. It was originally written in Python + Flask with a Vue.js frontend. page transitions were animated, ajax-triggered, and it was more SPA than SSR. I eventually got tired of waiting for my pretty animations to play out and rewrote it to be very boring, and it was a wonderful decision.

![Reading](/img/books-1.gif)
###### These gifs are of the second iteration of the project

Between Django and storing two versions of each book, the database is only 395 Mb. The original version was serving the thumbnails for the books out of the database too, but that was unecesary. I wised up and moved them to a static asset folder when migrating to Django.

![Search](/img/books-2.gif)

Search was implemented using basic SQLite full-test search, no fuzziness or anything.

Playing with the assets gave me some more practice with imagemagick and ffmpeg, which seems to come up naturally throughout a web developer's life. They're those technologies you never realize exist at first, but then you see them popping up in almost any project that involves media, and shudder to think what you would do without them. I'd probably be back using php's `imagecreatetruecolor()` and all its friends. No thank you.

Another motivation for the rewrite was that so much of my experience has been in Nodejs and php that I wanted a project to learn Python as a web development language too. Despite my aversion to complexity, I knew Flask and Django are popular, so I pulled up the docs to give myself experience in something more marketable.

This and the [bible research tool](/work/bible-research-tool) were both heavy exercises in text parsing. I've had enough experience with regex to weasel my way through megabytes worth of text.

## Tech stack

1. Backend: Python + Django
2. Frontend: plain javascript, about 25 lines in total, all of it optional
3. Database: SQLite
4. Deployment: Docker compose

I'm also happy anytime I get to experiment with docker. Having wasted my fair share of time wrangling the differences in environments and trying to compile applications for different architectures, learning how containerization simplifies those tasks was a breath of fresh air. Only regret there is the storage space it takes, constantly having to run `docker system prune` on my small Hetnzer box.

## Regrets

I don't think I'll be building any more SPAs anytime soon, except for where an employer asks for it. When it comes to the (minimal) scale and complexity of personal projects, my experience tells me to Keep it Super Simple.