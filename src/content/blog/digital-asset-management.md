---
title: 'Digital Asset Management'
description: 'A system for storing and retrieving files. Like a computer, but its not on your computer.'
pubDate: 'Jul 12 2023'
heroImage: '/img/explorer.jpg'
---

###### Note: As this was work done for a company, all images are of other systems, not the one I implemented.

This was the first project that I got to own at the first company I worked at. "Digital Asset Management", or of course, the DAM system. "Own" here means: have the final say in the system's architecture (and how it will fit into exiting systems) and modeling the domain.

Implementation was done with the help of one other very talented developer. I felt especially empowered on this team to ask for others' input on my design decisions to be sure I wasn't having someone else implement something that they didn't believe could handle the task.

The DAM system had a simple basic mission: dropbox-style file management. We weren't looking for concurrent editing or anything that would cause us to reach for CRDTs, but it did have a hefty set of features attached to that term "file management."

A the start of the project, I was handed some physical design mockups. It looked really good, and I was excited to get to be a part of it.

After more time in the project and experiencing all that goes into an interface, I have different thoughts about what to do with any future designs that are handed to me.

> Career lesson: don't assume designs have considered all use cases

The experience there was that the interface we had at the end still looked similar to the original, but with a multitude of buttons here and there to cover everything.

This project was revisted after months in production, and an entirely new frontend had to be built.

## Features
A short list I remember implementing:

1. Upload: both files and folders, automatic conversion, version creation, duplicate checking, etc.
2. Download: single files or zipped together
3. Delete: 30-day trash retention policy
2. Public and private file sharing, implying also:
    - Permission management
    - User groups
    - Application credentials for hosting other internal applications' digital assets.
3. Automatic tagging of images
4. Search
    - Fuzzy
    - using filters built into the search bar, e.g. file type, user uploaded, or within a specific directory
5. Email notifications
6. File versioning
7. Image rotation
8. Archive extraction

For as much hate as it's received over the years, php is suprisingly capable.

![Interface implications](/img/confusion.jpg)

This project has thus ruined casually looking at file browsers for me. I'm fascinated by all the complexity and design that packs a multitude of features into such a small space in front of you, all while remaining as discoverable as possible.

## Tech Stack

We were a pretty simple dev shop with an internal expected userbase in the 100s. Though it was designed to scale to thousands, I don't imagine the system faring well under the load of millions. All of this was considered when selecting the technologies used:
1. API: php
2. Frontend: Vue.js
3. Job scheduler: crond (Ol' Faithful)
4. Server: Apache
5. Searching: Elasticsearch
6. Blob storage: AWS S3
7. ML Tagging: Google Cloud Vision API
8. Async File processing: Lambda, using NodeJS
9. Metadata: existing MySQL instance

## Regrets

Someone at the beginning of the project suggested that it would be cool if S3 could somewhat mirror the folder structure of the system. NO NO NO don't go down this hole. It's a trap. It's not worth the overhead when implementing moving files between folders. Use UUIDs and you saved yourself a sprint cycle.

Single-page applications: They quickly get heavy and slow. [Server-side rendering is where the web started](https://hypermedia.systems/hypermedia-components/), and unsuprisingly it works incredibly well. Additionally, I find the development experience more logical.


## Highlights

A few particular things I particularly enjoyed implementing:

This was not merely the photographer's dumping ground for their SD card, but moreso it even served as a solution to any future project's blob storage needs.

A html widget was designed to be embeddable in future (and existing) applications that would allow them to not have any concerns about their file storage.

A custom context menu with various file operations. It's incredible how large the scope is for [what we demand in a file browser](https://en.wikipedia.org/wiki/File_Explorer#Extensibility):
![Wikipedia scope creep](/features.png)

Figuring out the logic of file selection and what the user intends when using `Ctrl+click` or `Shift+click`

The first time recursion was so logical and applicable to me was in the main function that uploaded files (and folders, recursively). It was a highlight to see all the same code work for folders autommatically.