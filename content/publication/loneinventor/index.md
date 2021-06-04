---
abstract: ""
slides: ""
url_pdf: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2962348
publication_types:
  - "2"
authors:
  - admin
  - Jürgen Mihm
  - Manuel Sosa
summary: >
  We challenge the notion that collaboration is always better than working
  alone. In our study using technological and design patents we find that the
  decomposability of the invention significantly moderates the effectiveness of
  the lone inventor. Particularly, tasks that are less decomposable relatively
  advantages the lone inventor. We also show that lone inventors working on
  non-decomposable inventions and who have collaborated widely in the past
  outperforms even teams. 
url_dataset: ""
url_project: ""
author_notes: []
publication_short: ""
url_source: ""
url_video: ""
publication: In Manufacturing & Service Operations Management
featured: true
date: 2018-03-01T00:00:00.000Z
url_slides: ""
title: Revisiting the Role of Collaboration in Creating Breakthrough Inventions
tags:
  - Product Design
  - Technology
  - Inventor teams
  - Innovation
projects: []
url_hbronline: https://hbr.org/2019/12/when-individuals-are-more-innovative-than-teams
image:
  caption: ""
  focal_point: ""
  preview_only: false
  filename: featured.jpg
url_paper: https://pubsonline.informs.org/doi/abs/10.1287/msom.2019.0858
publishDate: 2018-03-01T00:00:00.000Z
url_poster: ""
url_code: ""
doi: ""
---
## Pseudocode for measuring "decomposability" of a (utility) patent

Patent claims are written in such a strict way that the _subject matter_ of the claim - that is, the thing that the idea the claim protects - can be fairly easily identified. This in turn allows us to measure the degree to which the invention that the patent protects is **decomposable**. We say an invention is more decomposable (or modular) if it has more subject matters identified in this way. Conversely, it is less decomposable (or integral) if it has less subject matters identified in this way. (The intuition is that the more subject matters identified in an invention, the more one can apply ideas to individual parts of the invention without changing the rest). 

I use this approach to show that an inventor is more likely to create breakthroughs when working alone (compared to working with others) especially when working on integral inventions (see [paper](https://pubsonline.informs.org/doi/abs/10.1287/msom.2019.0858) and a shorter version on [HBR online](https://hbr.org/2019/12/when-individuals-are-more-innovative-than-teams)). 

I use [CoreNLP](https://stanfordnlp.github.io/CoreNLP/) to identify the noun phrase. 

***

1.	For each claim, identify whether it is independent or dependent by using a regular-expression search for the term “claim #”, where # signifies any number.
2.	If the claim is independent:
*	Break down the claim into individual words.
*	Tag each word in the claim with its type: noun, adjective, verb, etc.
*	Identify the root for each word (e.g., reduce the word “surfaces” to “surface”).
*	Identify the subject matter for the claim based on first-occurring noun phrase with adjectives 
(e.g., “outer free end”, “elastic strip”, “bioprosthetic mitral valve replacement”).
3.	If the claim is dependent:
*	Take the sentence starting after “claim #”—for example, from the text “A mitral valve replacement as in claim 1, wherein the base is…” use only “wherein the base is…”.
*	Return to the substeps of Step 2.
4.	Count the number of distinct subject matter in the patent.
