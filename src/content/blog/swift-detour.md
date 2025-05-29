---
title: 'A Swift Detour'
description: 'A quick experiment in productivity'
pubDate: 'May 29 2025'
heroImage: '/img/clipboard.jpg'
---
## Clipboard Management Made a Little Smarter
Today I came super close to losing something important that I had copied to my clipboard in the recent history. Thus, I began the hunt for a clipboard manager for Mac that was: 1) dead simple, 2) had just the smallest amount of organization, and 3) free.

Usually when I need a tool that I don't already have, I have probably heard someone mention a solution before on Hacker news. That was true in this scenario, but I didn't know of any one particular thing that had sparked my interest. I just knew this was a somewhat solved problem. So, I headed straight for https://hn.algolia.com and tried every combination of "Mac" and "clipboard manager" that I could think of, but each link that surfaced left me wanting. 
1. [ClipMenu](https://www.clipmenu.com/) appeared to be just what I wanted (at first), but it appears to only be distributed via dead dropbox links. 
2. [Maccy](https://github.com/p0deje/Maccy/blob/master/README.md) was ALMOST perfect, but I was looking to kill some time and venture into the AI world, so I decided to write my own.
3. [Do self-respecting developers still use chrome when given a choice?](https://chromewebstore.google.com/detail/clipboard-history-copy-pa/ipdbhhkchfhihbaongpicbkahpaiacnj)
4. [DoubleMemory](https://doublememory.com/), a recent contender, can do too much.
5. [Same with Pastebar](http://pastebar.app)

But they're all good products in their own right. Just not everything that I want.

By the way, if you are looking for a clipboard manager, go ahead and use Maccy. Mine is wholly unfinished, and I'm not sure I'm desperate enough to pick it back up.

## But
Mine has ✨AI✨. In reality, I just wanted an excuse to see if all the hate on XCode was deserved and how easy it is to implement something with Ollama.

After a quick dinner date with Google AI Studio and Gemini Pro 2.5 preview, [ta-da](https://git.ramseyer.dev/abe-org/ClipboardHelper).

##### Quick Note
This is something that I don't want to share with the world, but anyone reading the site is welcome to see it. For that purpose, I set up a Gitea server yesterday (which I would recommend for how painless it is). I think I set the security settings good enough that I can provide the username and password here for a guest account to check out my "hidden" projects.

<details>
    <summary>Guest Credentials</summary>
    <pre>username: guest
password: qipjup-sikrad-ciphU6</pre>
</details>

![demo video](/img/clipboard.gif)

I spent about one hour on this and was able to make a clipboard history manager that will tag each item using a local Ollama server. I'm starting to see what the vibe coders are excited about, but even after an hour, I know I have little ability to maintain this application. I still know next to nothing about Swift, but this was a very cool proof-of-concept. I would have little trust in any company that trusts their developers to work _primarily_ in this way with little understanding of their tools and resulting code. I really hope that the people learning to code these days are still taking the time to learn the fundamentals.

Overall, this was a very enlightening experience to see just how easy it is to make something that has 1) works 2) is in an unfamiliar territory, and 3) has potential for monetization. A productive late-afternoon!

And yes, the negative press for XCode is well-deserved.
