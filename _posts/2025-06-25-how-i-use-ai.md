---
title: "How I use LLMs as a clinical AI researcher and developer"
collection: blog_posts
description: |
    Biomedical research requires hard data and grounded facts to support experimentation.
    Development requires creativity and quick iteration. 
date: 2025-06-25
layout: post
note: false
tags: tech
published: false
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

### How I used to do it

At the end of the day, this can be summarized into a pretty complicated query:

```
("interrater" OR "inter-rater") AND ("reliability" OR "agreement" OR "variability" OR "disagreement") AND ("annotating" OR "annotations" OR "contouring" OR "contours" OR "segmenting" OR "segmentation") AND ("MRI" OR "MR" OR "magnetic resonance imaging")
```

You get the gist. This is a boring work. What's more, I would have to filter results to ensure that they referred mostly to scientific publications (or use Google Scholar, which is from my experience a bit more limited). This is all work which is manageable, but it is also work which is not particularly fun to do.

### How I do it now

I do an initial Google search with the best terminology I can find without getting lost with a never-ending search query. If I am having little luck, I go to the flavor-of-the-month chatbot and activate the "Search" feature (in ChatGPT this is called "Search the web", DeepSeek has "Search"). I don't know exactly what they do under the hood (I assume they convert my natural language query into a set of search queries which they fire into a nice search engine) and voilà! I get a bunch of usually useful results. Then, I can read the results and confirm what is and isn't useful.

**Things I don't recommend:** using the summaries provided by chatbots can be a shot in the dark. They may be good, but they may also be rubbish. And yes, I have tried Perplexity (including Deep Research) - I found that for scientific research it is a bit lacking. What is also a bit complicated is to try to restrict these bots to look for information in specific websites - while some are becoming really quite good at it, it can still be a bit complicated to have them zero in on the right information.

## Code reviews

This is a fairly popular application - ask an LLM to detect some possible deviations from an ideal implementation. This can be performed with your favorite LLM-assisted IDE, but you can also use the traditional online chatbot to do it.

Typically, after implementing something complicated, I cannot know for certain whether or not it is correct: this is especially the case when implementing neural networks or similar methods. I want to be as certain as possible, but running a training session which can last hours or even days is not something I want to do - plus, it is super wasteful.

### How I used to do it

I would very carefully read through the code and double check everything. Then, I would finally run some test runs, and upon detecting deviations from the expected behavior, I would try to debug the code. 

This is where it would get tricky - I have a complex system which does not produce an error; it just behaves differently from the expected. Debugging these kinds of issues is not trivial and can take a long time.

### How I do it now

I still review everything carefully, and I still double check everything. However, before running any tests, I ask the LLM - "I am implementing this method which does X, Y and Z. My expectation from the method description is that A, B and then C should happen. Could you check that my code is doing this?"

The good thing here is that, if there are any significant mistakes, the LLM is usually capable of picking them up. For instance: sometimes the implementation for a mathematical function is missing a sign, or the wrong variable is used in a calculation. The LLM is usually fairly good at picking up these things. While it can miss some things, it saves me the trouble of having to detect all of the possible mistakes.

**Things I don't recommend:** replacing regular code reviews or replacing testing with LLM-based code reviews. There is a reason these are still largely done by people! Some systems are critical enough that I would not want to risk having just an LLM perform code reviews. Plus, writing unit tests is still a good thing to do "manually" - my experience has shown me that LLMs are not really good at doing this.

## Ideation

LLMs can be good to pick your ideas apart. Combined with the "Search" functionality I mentioned earlier, they can be tremendous in understanding what is and isn't available and what can be interesting research avenues. This is probably where LLMs are best aligned with what is performed both in academia and in industry: determining what are relevant research questions and what constitutes a worthwhile direction to pursue.

### How I used to do it

A new idea would form in the back of my mind. I would write it down, try to think of potential pitfalls and holes, and come back to it at a later stage. I would probably discuss it with some colleagues or friends to get a good idea of what is and isn't possible.

### How I do it now

I have a simple candid discussion about my idea with the LLM. I have no structured format for this, but I want to know specifically: what are the potential pitfalls? What has been done on this topic before? What is left to be done? 

Ultimately, this exercise ideally leaves me in a good place to answer the following question: what are the most important questions to ask about this topic? Then, I can have a much more informed discussion with colleagues and friends. Mind you: I don't stop talking with people, it's just that the discussion I have with them is much better informed.

**Things I don't recommend:** asking the LLM to generate a research question from thin air. This is quite complicated and it is unlikely to be aligned with what you can actually achieve. Remember: there are many interesting research directions, but it is probably you (or your team) who will have to perform the actual work.

## Local testing of LLMs

