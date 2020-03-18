---
layout: post
authors: [ken_bostoen, elke_heymans]
title: "Vuejs composition api and GraphQL using apollo"
image: /img/chatbot.png
tags: [Vuejs, GraphQL, Apollo, Composition api, Frontend, Vue 3, Javascript]
category: Frontend development
comments: true
---

> Chatbots, they seem to be everywhere, and yet, there are a lot of people who have no idea what they are.
> I came home one day in October and told my parents and sisters I was building a chatbot at work.
> Their reaction: "You're building a what now?". 
> So I took ten minutes to explain them what a chatbot is and does.
> In the end, they just said "So... It is a computer person?". <br/> <br/>
> This post will feature a high-level explanation of what chatbots are and what they do, as well as a deep dive into chatbot providers and a technical implementation. 
> In the end, we'll look at a practical case of a chatbot: FleetBot Dina. 

# Table Of Contents

* [Introduction](#introduction)

# Introduction
The concept of chatbots has existed ever since Alan Turing designed the Turing test in 1950, with the original concept of the test dating back to 1936.
The question asked in this test was "Can machines think?". 
The test proposes a way to measure if the testee can know whether he's talking to a human or a machine.
Joseph Weizenbaum was the first to design a real chatbot, ELIZA, in 1966 at the MIT AI laboratory, which he called a 'chatterbot'.
Even though it failed the Turing test, the main idea behind a chatbot has since then remained the same: recognise what a user says using pre-programmed keywords and phrases, and respond accordingly.

<img alt="ELIZA" src="{{ '/img/2020-02-24-Chatbots-Introduction-and-a-Practical-Case/ELIZA.jpg' | prepend: site.baseurl }}" class="image fit" style="margin:0px auto;">

Technology has obviously evolved a lot since 1966. 
Modern chatbots do not only look at keywords and phrases anymore.
They use a technology called [Natural Language Processing](https://mobilecoach.com/chatterbots-6-what-is-natural-language-processing/){:target="_blank" rel="noopener noreferrer"} (NLP) and Understanding (NLU) to understand the meaning behind what a user says. 
NLU uses complex algorithms to analyse the input, not only with predefined keywords but by using various aspects of the language and the sentence structure of the given input.

This way, not only can a chatbot understand what a user says, but it can also do a sentiment analysis and extract useful information out of the input.
An example, when the user says *"Damn, someone drove into my **Car Brand** earlier today, but it wasn't my fault. I don't know what I should do now."*, the chatbot would know that the user was quite angry, he had an accident, and he drives a **Car Brand**. 
The bot's response could be: *"I hope you're okay. Here is a list of garages you can go to. Since it wasn't your fault, insurance will help you figure this out."*

<img alt="NLP" src="{{ '/img/2020-02-24-Chatbots-Introduction-and-a-Practical-Case/NLP.png' | prepend: site.baseurl }}" class="image fit" style="margin:0px auto;">

In 2006, the world saw the first big tech company launch a chatbot called Watson.
IBM's Watson went on to winning a game of "Jeopardy!" against all-time champions Ken Jennings and Brad Rutter in 2011.
Since then, tech giants like Apple (Siri), Google (Google Now), Amazon (Alexa) and Microsoft (Cortana) have all launched their own personal assistant chatbots with their respective NLPs.
In Belgium, Antwerp company [Chatlayer](https://www.chatlayer.ai){:target="_blank" rel="noopener noreferrer"} provides a custom platform to build chatbots. 
They use whichever NLP is best in a given language.
For Flemish & Dutch, they built a custom NLP. 

Like all chatbots, these personal assistants have a specified set of use cases, setting alarms, playing music, reading the weather report, telling jokes,... 
If they don't know the answer to a question, they will usually just look up whatever you asked on the internet, and give you the best response.

# Essential terminology
These are a few terms you should know when studying or working with chatbots.
They will be used throughout this blog.

* **Natural Language Understanding**<br/>
> NLU is the Artificial Intelligence (AI) which tries to understand the meaning behind what a user says.
> It can do a sentiment analysis, extract relations between words and phrasing, do semantic parsing,...
* **Natural Language Processing**<br/>
> NLP consists of NLU, along with extra factors like syntactic parsing. 
> The key takeaway here is that NLP translates the user input to machine language and determines what a user has said.
* **Natural Language Generation (NLG)**<br/>
> NLG comes after the computer has understood the meaning behind the input and formulates an answer. 
> This answer is usually predefined, but can vary depending on the input and the entities the bot has saved so far. 
* **Entities**<br/>
> Entities are data that a chatbot can save during a conversation, e.g. your car brand, your tire type,...
* **Expressions**<br/>
> An expression is anything that a user sends or says to the bot.
* **Intents**<br/>
> The intent is the purpose behind a user's message, e.g. does the user ask for a garage, does he want to know about how to refill his AdBlue,...
* **Context**<br/>
> A context is used when you expect the user to reply to a bot question.
> By using contexts, you can direct the conversation into a certain flow, helping both the user and the computer along.



# Conclusion
After working with chatbots during the past 6 months, I'm proud of what we've achieved so far. 
The FleetBot is being actively tested at JWorks and looking to go live for all Ordina Belgium employees.
Because of working closely with Chatlayer on the FleetBot project, we have initiated a partnership for future chatbot projects.
There already are a number of interesting projects coming up that we're happy to be part of.
Having tested many chatbot providers, we can confidently make an assessment of which one would be best in any use case.

What I'm most excited about is the versatility of chatbots. 
Want one in Telegram or Slack? <br/>
No problem, we can build that connection! <br/>
Want one that speaks Chinese, German and English? <br/>
Can do!

Do you think your company could use a chatbot to raise user satisfaction, reduce your FAQ workload, or for anything else it could help out with?
Get in touch with [Frederick Bousson](mailto:frederickbousson@ordina.be?subject=[Chatbots]%20Interest%20in%20chatbot%20project)! <br/>
We can help you evaluate if a chatbot is indeed the way to go for your specific case and choose the correct provider for your needs.
After that, we will assist you in building the bot and build all necessary chat client connections.

# Resources
* [Chatbot History](https://mobilecoach.com/chatterbots-2-history-of-chatbots/){:target="_blank" rel="noopener noreferrer"}
* [Watson Jeopardy!](https://www.nytimes.com/2011/02/17/science/17jeopardy-watson.html){:target="_blank" rel="noopener noreferrer"}
* [NLP Intro](https://becominghuman.ai/a-simple-introduction-to-natural-language-processing-ea66a1747b32){:target="_blank" rel="noopener noreferrer"}
* [NLP vs NLU](https://nlp.stanford.edu/~wcmac/papers/20140716-UNLU.pdf#page=8){:target="_blank" rel="noopener noreferrer"}
* [10 Lessons Learned From Building Big Chatbots](https://www.chatlayer.ai/wp-content/uploads/downloads/big-bots-guide-20190626.pdf){:target="_blank" rel="noopener noreferrer"}