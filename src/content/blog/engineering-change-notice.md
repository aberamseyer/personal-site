---
title: 'Engineering Change Notice System'
description: 'A system for approving engineering change notices.'
pubDate: 'Aug 25 2023'
heroImage: '/img/vuetify.png'
---
###### Note: As this was work done for a company, all images are of other systems, not the one I implemented.

This project was given to me to own around early 2020. I remember it was one of the first projects I worked on almost exclusively from home.

This project was essentially a  pdf viewer whose goal was to centralize documents the company needed multiple people to approve. This was currently being done through a long email chain of "Reply-all"s, so everyone was thankful for the possiblity of that going away.

While not as feature-rich or complex as the [DAM system](/work/digital-asset-management) I had worked on previously, the designer I was working with was more experienced and understood how to provide components from a library rather than inventing his own.

The system was essentially two views:
1. An L1 table view with a left-hand sidebar for different filtered views of the data
2. An L2 view where the pdf in a table entry could be reviewed, manipulated, and "approved"

## Features
1. Regularly synchronization of documents needing approval into the system
2. Seeing each document's summary of progress, along with more details of the document itself
3. Ignore unnecesary documents that didn't actually need approval
4. Basic PDF page re-ordering and rendering in the browser
5. Email notifications for those needing to approve documents with deep links to the L2 view

## Tech Stack
1. AWS Appsync
    - Authentication
    - API: GraphQL
    - Backend–Lambda, using NodeJS
2. Database: existing MySQL instance
3. Frontend: Vue.js + a CSS framework, I think it was called Materialize but I may be mistaken
4. PDF processing: PDF.js
5. Job Scheduler: Lambda event scheduler
6. Blob storage: AWS S3

## Highlights

I got to make a system that looked amazing! While the design of previously implemented systems were somewhat modern, this was the first time I got to deploy an entire website through Webpack-ing a SPA framework. Consequently, the frontend ran faster and technologies played together better because the they were being bundled and deployed as intended.

## Regrets

Don't try to re-solve the n+1 problem. I at one point had a perfectly working system that should have been extremely snappy, but it just became slower and slower the more documents were fed into the system. Pagination was implemented as a band-aid fix, but it still wasn't as performant as I knew it would be if built with a simpler RESTful API. In the world of NoSQL it may have worked, but in the relational database schema I had designed, it was non-trival to fix on my own. I considered drop-in systems like [Hasura](https://hasura.io) for the API, but the added tech stack fragmentation was not desirable to the client.

Refresh tokens don't play that nicely in AppSync. I would wait for the technology to mature more before trying to build a system around it. I fell for the excitement of it while attending the previous AWS re:Invent conference.