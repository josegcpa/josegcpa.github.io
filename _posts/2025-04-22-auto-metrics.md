---
title: "Auto-METRICS - a proof of concept"
collection: blog_posts
description: Automatic assessment of methodological quality in radiomics research
date: 2025-04-22
layout: post
note: true
tags: apps
---

Recently, I received my first (obvious) LLM peer review. It was quite blatant. What's worse: it wasn't good - at all! Funnily enough, I had been working on something related: Auto-METRICS, a tool for automatic standardised assessment of scientific research quality in radiomics research using the [METRICS](https://insightsimaging.springeropen.com/articles/10.1186/s13244-023-01572-w) framework.

To show its utility, we make use of two unique, recent datasets on reproducibility in radiomics studies - Akinci D'Antonoli et al. (2025) and Kocak (2025). Together, they feature really good set of METRICS ratings - for different levels of expertise and training - for more than 50 publications. This allowed us to systematically compare human and LLM raters.

The main takeaways:

- Human raters agree with LLMs at the same rate that they agree with other human raters ✅
- Prompt iterations: clarifying radiomics guidelines can lead to better agreement with human raters. However these improvements were quite limited! 📈
- Too nice: LLM ratings tended to be slightly higher than those offered by human raters 😇 

I tested our tool - Auto-METRICS - [here](https://autometrics.josegcpa.net/) (all you need is a *free* Google Gemini API key) and found it really helpful to get an initial assessment for METRICS which I can easily confirm. The key? Enhance, don't replace - having good initial ratings was super helpful in getting a final, human-based classification.

Curious? Read more about Auto-METRICS at [medRxiv](https://www.medrxiv.org/content/10.1101/2025.04.22.25325873v1).
