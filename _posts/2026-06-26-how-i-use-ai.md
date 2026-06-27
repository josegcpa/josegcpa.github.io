---
title: "How I use LLMs as a clinical AI researcher and developer"
collection: blog_posts
description: |
    Biomedical research requires hard data and grounded facts to support experimentation.
    Development requires creativity and quick iteration. 
date: 2026-06-26
layout: post
note: false
tags: [tech, science]
published: true
---

I am not going to say that everyone is using LLM-based tools in their research or development activities. However, it sure is hard to run into someone who doesn't know about them. LLMs have a lot of potential benefits in both fields - but they also come with potential pitfalls. Knowing when to go for different tools can prove really helpful when you frequently hop between two different worlds. 

I am writing this down as a fluid and living guide for myself and others. I can't claim that this is the best possible guide for these tools, but oftentimes these tools have saved me a significant amount of work. I will focus on a few things: literature search, code reviews, ideation, and even local testing of LLMs.

## Literature search

Now, I can already predict a reasonable criticism: are you performing _search_ with _LLMs_? What are you, some sort of a _moron_?

Well, no. At least not always.

Sometimes I have a complex research question to answer. Something like "what is the expected inter-rater agreement between radiologists annotating the prostate in MRI". Now, a big problem here is that traditional search engines are very reliant on keywords - this leads to some problems. For example:

* "inter-rater" and "interrater" are used interchangeably
* "inter-rater agreement" can be also referred to as "inter-rater reliability", or studies can measure instead "inter-rater variability" or "inter-rater disagreement"
* "annotating" can be called "contouring" or "segmenting"
* "MRI" can also be referred to as "MR" or "magnetic resonance imaging"

**How I used to do it:** at the end of the day, this can be summarized into a pretty complicated query:

```
("interrater" OR "inter-rater") AND ("reliability" OR "agreement" OR "variability" OR "disagreement") AND ("annotating" OR "annotations" OR "contouring" OR "contours" OR "segmenting" OR "segmentation") AND ("MRI" OR "MR" OR "magnetic resonance imaging")
```

You get the gist. This is a boring work. What's more, I would have to filter results to ensure that they referred mostly to scientific publications (or use Google Scholar, which is a bit more limited from my experience). This is all work which is manageable, but it is also work which is not particularly fun to do.

**How I do it now:** I do an initial Google search with the best terminology I can find without getting lost with a never-ending search query (`&udm=14` is pretty helpful if I want to avoid AI generated results from Google). If I am having little luck, I zoom in on Google Scholar, which now has a pretty good [Labs](https://scholar.google.com/scholar_labs/search) feature which allows you to perform semantic searches - most of the times this allows you to get to some pretty relevant hits. [Semantic Scholar](https://www.semanticscholar.org/) is a good alternative for this, much like [AlphaXiv](https://www.alphaxiv.org/). Finally, if all else fails, I go to the flavor-of-the-month chatbot and activate the "Search" feature (in ChatGPT this is called "Search the web", DeepSeek has "Search"). I don't know exactly what they do under the hood (I assume they convert natural language queries into a set of search queries which they fire into a nice search engine) and voilà! I get a bunch of usually useful results. Then, I can read the results and confirm what is and isn't useful. 

**Things I don't recommend:** using the summaries provided by chatbots. They may be good, but they may also be rubbish. It's a shot in the dark. And yes, I have tried Perplexity (including Deep Research) and other similar research-oriented chatbots - I found that for scientific research it is a bit lacking, they try to search for _alternative questions_ when an answer for _your question_ is not available from the literature. What is also a bit complicated is to try to restrict these bots to look for information in specific websites - while some are becoming really quite good at it, it can still be a bit complicated to have them zero in on the right information.

## Code reviews

This is a fairly popular application - ask an LLM to detect some possible deviations from an ideal implementation. This can be performed with your favorite LLM-assisted IDE, but you can also use the traditional online chatbot to do it.

Typically, after implementing something complicated, I cannot know for certain whether or not it is correct: this is especially the case when implementing neural networks or similar methods. I want to be as certain as possible, but running a training session which can last hours or even days is not something I want to do - plus, it is super wasteful.

**How I used to do it:** I would very carefully read through the code and double check everything. Then, I would finally run some test runs, and upon detecting deviations from the expected behavior, I would try to debug the code. This is where it would get tricky - I have a complex system which does not produce an error; it just behaves differently from the expected. Debugging these kinds of issues is not trivial and can take a long time.

**How I do it now:** I still review everything carefully, and I still double check everything. However, before running any tests, I ask the LLM - "I am implementing this method which does X, Y and Z. My expectation from the method description is that A, B and then C should happen. Could you check that my code is doing this?" The good thing here is that, if there are any significant mistakes, the LLM is usually capable of picking them up. For instance: sometimes the implementation for a mathematical function is missing a sign, or the wrong variable is used in a calculation. The LLM is usually fairly good at picking up these things. While it can miss some things, it saves me the trouble of having to detect all the possible mistakes.

**Things I don't recommend:** replacing regular code reviews or replacing testing with LLM-based code reviews. There is a reason these are still largely done by people! Some systems are critical enough that I would not want to risk having just an LLM perform code reviews. Plus, writing unit tests is still a good thing to do "manually" - my experience has shown me that LLMs are not really good at doing this. Unless you want a lot of "fallback" tests that are not really testing anything.

## Ideation

LLMs can be good to pick your ideas apart. Combined with the "Search" functionality I mentioned earlier, they can be tremendous in understanding what is and isn't available and what can be interesting research avenues. This is probably where LLMs are best aligned with what is performed both in academia and in industry: determining what are relevant research questions and what constitutes a worthwhile direction to pursue.

**How I used to do it:** a new idea would form in the back of my mind. I would write it down, try to think of potential pitfalls and holes, compare it with the current state of the art using some meaninful reviews, and come back to it at a later stage. I would probably discuss it with some colleagues or friends to get a good idea of what is and isn't possible. 

**How I do it now:** I have a simple candid discussion about my idea with the LLM. I have no structured format for this, but I want to know specifically: what are the potential pitfalls? What has been done on this topic before? What is left to be done? Ultimately, this exercise ideally leaves me in a good place to answer the following question: what questions are worth answering? Then, I can have a much more informed discussion with colleagues and friends. Mind you: I don't stop talking with people, it's just that the discussion I have with them is much better informed. I know a lot of people use [NotebookLM](https://notebooklm.google/) for this but I never really found it that useful on top of what I already do.

**Things I don't recommend:** asking the LLM to generate a research question from thin air. This is quite complicated and it is unlikely to be aligned with what you can actually achieve. In general, LLMs are not necessarily good at coming up with new ideas; they are however quite good at broadly synthesizing the current research landscape. In general, it is worth remembering that there are many interesting research directions, but it is probably you (or your team) who will have to perform the actual work.

### A small note on interacting with chatbots and people

I have come to notice that getting a good answer requires some back and forth to clarify meaningful aspects of your baseline idea. When you interact with a colleague or a long-term collaborator, you can know for a fact that there is a shared vocabulary which makes a lot of the conversation implicit. With chatbots, that is not always the case. Chatbots have to be led by you, and you need to be explicit about what you want - the shared vocabulary is simply not there, and you need to specify it more actively than you would with a human.

## Other tools which might be interesting for you

There are a lot of AI tools out there which I don't use or care for. I compiled below a small list of tools which I think can be useful for other people or which made me go "huh, neat":

* **Visual literature graphs:** there are some platforms which are capable of making a large connected graph of scientific manuscripts and represent it visually ([Connected Papers](https://www.connectedpapers.com) and [LitMaps](https://www.litmaps.com/) are pretty good examples of this). This can be nice to try finding papers which are related to a specific one, but I find that I don't really use them that often. I find [Semantic Scholar](https://www.semanticscholar.org/)'s "Related papers" tab much easier to use.
* **Literature synthesis:** I am keeping this separate from the "literature search" section because I think that there is some danger in merging the two, but some people might disagree! Having said that, there are plentiful AI literature synthesis tools out there ([Elicit](https://elicit.com/), [NotebookLM](https://notebooklm.google/), [Consensus](https://consensus.app/) or [SciSpace](https://scispace.com/) come to mind) which I believe can be useful to quickly get you close to an overview of a topic. SciSpace in particular even has a PRISMA-based systematic review workflow. I don't really use them, but that's mostly because I like being in control of that part of the process, not because I found some deep issue with these tools.
* **AI Notetakers for online meetings in general:** I think these can be useful but I haven't found the point for them. They end up generating summaries I don't care to read and at times they hallucinate quite heavily. But I know they are quite popular and they might be a good way of at least keeping a record of what you've been doing if you attend many meetings. In general, I really don't like how closed off and subscription-dependent these tools are.
* **Writing and editing papers and grants:** I think there are some nice programs which focus on clarity, structure and grammar.[Grammarly](https://www.grammarly.com/) is unquestionably the most popular tool for this despite comically [poor strategic decisions](https://www.nytimes.com/2026/03/13/opinion/ai-doppelganger-deepfake-grammarly.html), but there are some cool self-hosted alternatives: 
    * [Harper](https://writewithharper.com/) runs locally on your machine so you don't have to worry about sending your data abroad (the setup can be [a bit annoying](https://github.com/Automattic/harper/issues/3504), but I think this should be fixed by the time you read this), and it integrates seamlessly with Obsidian (**cons:** it only works in English as far as I can tell)
    * [LanguageTool](languagetool.org/dev) is another pretty cool solution (I found it more straightforward to use out-of-the-box than Harper): when using any of their add-ons, you can pick using either their servers or your own locally hosted LanguageTool. Setting it up requires using the command line but the guides are very clear (in MacOS it amounts to using two `brew` commands)
    * **Beware:** self-hosting with either of these does not appear to get you to a good place in terms of AI-powered rewriting and those sorts of things. They mostly do standard grammar checking. I recently developed/vibe-developed an [Obsidian extension](https://github.com/josegcpa/elf-obsidian-plugin) to do this, but this is my own personal tool which I tested for *my own stuff*.
* **There are also some neat AI-powered LaTeX editors:** [Prism](https://prism.openai.com/), which was unfortunately recently acquired by OpenAI, is probably one of the most popular ones. I use it mostly because it doesn't have the compilation time caps that other editors (i.e. Overleaf) have, but I don't use the AI features (despite them _really_ trying to).
* **AI-powered slideshow presentation generators:** I have tried one or two but I find that the presentations are oftentimes really generic.

## What can you do with this?

Experiment! I have tried to compile some information here that might be useful for you, but knowing the names of tools is only the starting point - you will not be able to know what works for you until you try it out. And remember - this is a starting point, not a destination. Identify the painpoints in your research workflow, get a sense of the things you deeply care about and enjoy doing, and continue exploring what new tools and techniques work best for you. 