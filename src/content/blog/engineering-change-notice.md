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
    - Authentication: existing auth layer
    - API: GraphQL, using data resolvers connected to MySQL
    - Backend: Lambda, using NodeJS
2. Database: existing MySQL instance
3. Frontend: Vue.js + a CSS framework, I think it was called Materialize but I may be mistaken
4. PDF processing: PDF.js
5. Job Scheduler: Lambda event scheduler
6. Blob storage: AWS S3

## Highlights

I got to make a system that looked amazing! While the design of previously implemented systems were somewhat modern, this was the first time I got to deploy an entire website through Webpack-ing a SPA framework. Consequently, the frontend ran faster and technologies played together better because the they were being bundled and deployed as intended.

## Regrets

Be carefule about the n+1 problem! It's one of the most obvious footguns out there for someone coming from a REST background, and unfortunately it threw me for a loop for a couple days. There were some slowdowns due to the way the database resolvers were implemented, but nothing too egregious. Pagination was implemented to mitigate it, and the result was something comparable to a typical REST-ful API. Additionally, other people have success avoiding it with eager querying, batching requests, caching data (redis/memcached), and [certain libraries](https://github.com/graphql/dataloader). While in the world of NoSQL performance may have been free, in a relational database, it was not as smooth of an implementation. I considered drop-in systems like [Hasura](https://hasura.io) for the API, but the added tech stack fragmentation was not desirable to the client.

Refresh tokens did not play very nicely with me in AppSync. Today, I would wait for the technology to mature a couple years before trying to build a system around it. I used it after receiving inspiration from a recent AWS re:Invent conference, and I do not regret that choice, but my immediate feeling while wokring was to avoid recommending it as a magic all-batteries-included solution to a system.