---
layout: post
title: "Hosting Local Open Weight LLMs for Chat & Coding"
date: 2026-03-09
---

*Throughout this blog, I will continue to mention facts and events that happened. These are ground truth and there's no way to view them in any other way. However, I will also share many of my different opinions- these are "Strong opinions, weakly held" ([link for further reading](https://medium.com/@ameet/strong-opinions-weakly-held-a-framework-for-thinking-6530d417e364)). Since these are personal opinions, anyone can disagree or argue with them, which is why I will be putting a marker **PO** on these to segregate them from facts and events.*

It all started from the notion of OpenAI colluding with the US government, and Anthropic's refusal to participate in that. For many of us, chatbots are equivalent to ChatGPT. This is where it all started and what we are used to by default. I had installed ChatGPT so long ago on my phone that I never felt curious to see what other options were out there in the world. Part of the reason is that I am not a power user of chatbots and/or coding agents. **PO:** One shouldn't pay for chatbots for coding support unless the company is paying for it. Whenever I do make use of these features, I do it by copy/pasting like a peasant in the browser to get my target output. I was not going to spend a dime on my personal pet projects- they are not that important.

Anyway, I am getting derailed. It all started there, when I decided to leave OpenAI and move to Anthropic to support their stance. Around the same time, news broke out on [Qwen 3.5](https://qwen.ai/blog?id=qwen3.5). Open weight LLMs have been worth the hype for quite some time- it just never was on my radar to really try them out. My barriers were, in order: lack of good computational power devices, enough time, an established ecosystem to try these out, and the availability of good enough models (not cosidering LLaMa because we all know how good it really is, **PO**).

---

**LM Studio & Qwen**

However, this time I thought maybe I should give it a try. It was a fun weekend project, easy enough to be done in a single sitting within 2–3 hours. The plan was simple: download Ollama or [LM Studio](https://lmstudio.ai/), install a locally downloaded open source LLM model, and see how it performs compared to commonly used chatbots (ChatGPT/Claude). The reason I mentioned Qwen is that they released Qwen 3.5 with many model sizes- specifically, the 2B or 4B version would run okayishly on my Mac Mini.

And it did. It was basically point-and-click to download the DMG and install LM Studio. I didn't go with Ollama because I saw some user errors when installing Qwen 3.5 on Ollama, likely because the model was very new. LM Studio also has an easy GUI to work with. I downloaded Mistral first because for some reason Qwen wasn't working on my Mac Mini initially. Later I found that the GGUF version worked fine, so I used that to download Qwen 3.5 4B.

---

**The Magic**

It was really awesome. There I was, chatting with a bot hosted completely locally, without paying anyone a single cent. The token speed and inference were very good with Mistral. With Qwen, it was spending a lot of time thinking- which was overall a good thing, as it had better clarity on the questions I was asking- but I turned that off later because I didn't really need it at this point.

![image-of-lmstudio-qwen](/assets/img/blogs/hosting-llm-1.png)

Worth noting: since it's a 4B parameter model, I did not expect the most perfect reasoning for my queries. Basically, if it could parse normal text and make sense of my commands, that would be good enough for me, because I plan to have it do some custom tasks that don't require meticulous design- just some basic understanding would work. (Additionally, it also supports vision, so it's really helpful for parsing simple things like a photo of a receipt.)

---

**Temu Cursor**

My next question was: okay, I can host and run a local LLM and chat with it- but what would I actually use it for? The most common scenario was coding support. I've seen people use Claude Code or Cursor, but they are all paid. Could I potentially recreate even a weaker version of this without spending anything? Turns out I can. Within VS Code on my Mac Mini, I installed the extension [Continue.dev](https://www.continue.dev/), which uses locally hosted LLMs as a coding agent. I just connected it to the API server endpoint running in LM Studio, and voilà- there I was, using a coding agent for my projects.

![image-of-continue-dev-vscode](/assets/img/blogs/hosting-llm-2.png)

---

**Temu ChatGPT**

Okay, now that I could comfortably host and run a local LLM and chat with it, I started running into some next-level walls. I tried asking it to search for the latest info- it couldn't. This is because it's more like a calculator; it's just a text inference machine and doesn't have any tools to access external features. I also tried accessing it from my phone, as I would naturally do, and expected it to work since my phone and Mac Mini are on the same network- but there was no easy way to do it.

Also, I realized I'm not always sitting at my PC to chat; I need access from my phone too. At this point, [Open WebUI](https://openwebui.com/) came to the rescue. It's basically a frontend for chatbots where, on the backend, I can point it to any LLM model I want- in my case, Qwen via LM Studio on the Mac Mini. Open WebUI needs to be hosted via Docker and requires constant uptime like a server. And what could be a better option than a NAS?

Last Black Friday I already got a NAS for photo storage. It has Docker up and running, with an ad blocker running constantly. I just added a new container for Open WebUI and pointed the OpenAI-compatible API endpoint to my local LM Studio server. Noice! Now I can chat just like with ChatGPT, using a locally hosted LLM, without any data being sent to any third-party server.

So right now, I can use a ChatGPT-like interface to talk to my PC using a locally hosted LLM, and also use VS Code with agent-supported coding. I would say this is pretty awesome, because it didn't cost me anything to build this ecosystem- I used all of my existing tools to set it up. And a huge thanks to the open source community for making these models available for regular people to use and not locking them behind corporations, because in the end all of this is built upon the data and information provided by humans for so long.

---

**Questions**

**PO:** Given all of this, I'm curious- how long can these companies keep competing when there are okayish open source solutions already available? What's the end game when people can have locally deployed agents handling their everyday tasks? Yes, historically, even though people can run their own server solutions at home, the largest and most reliable products always come from big names. But the monopoly the current market has may not justify the insane valuations these companies are trying to sell. Something has to give. Anyways, for now, we have got a lot to explore!