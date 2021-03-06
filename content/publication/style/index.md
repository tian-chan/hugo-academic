---
abstract: Products combine function and form. This paper focuses on product form. We combine state-of-the-art clustering techniques with experimental validation to identify styles (groupings of new product designs of similar form) among the more than 350,000 U.S. design patents granted from 1977 through 2010. Thus we compile, for the first time, a rich data set of styles that can serve as an empirical platform for a rigorous study of the role played by product form in new product development. Building on this platform, we analyze the determinants of “style turbulence”—the year-to-year unpredictability of changes in a style’s prevalence. We find that (i) style turbulence follows a U-shaped relationship with respect to function turbulence (the turbulence of product functions associated with a given style), and (ii) style turbulence increases over time. We discuss the implications of these findings for managing design in new product development.
slides: ""
publication_types:
  - "2"
authors:
  - admin
  - Jürgen Mihm
  - Manuel Sosa
summary: >
  We show how one can identify styles (categories of product design that are
  perceived to be similar) using design patents. Using this data set we show
  that (i) style turbulence (unpredictable changes in style) is increasing over
  time, and (ii) technological turbulence (unpredictable changes in technology)
  have a U-shaped relationship to style turbulence.  I use this data platform to
  study other questions (see e.g., "Anchored Differentiation"). 
links:
- name: Paper
  url: https://pubsonline.informs.org/doi/abs/10.1287/mnsc.2016.2653
url_dataset: "https://drive.google.com/open?id=1s6iJnyxDbWrNXFv0RCjiLY3ubK2eIxZ7"
url_pdf: "https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2428744"
author_notes: []
publication_short: ""
url_source: ""
url_video: ""
publication: In Management Science
featured: true
date: 2018-03-01T00:00:00.000Z
url_slides: ""
title: "On styles in product design: An analysis of US design patents"
tags:
  - Product Design
  - Style
  - Innovation
projects: []
image:
  caption: ""
  focal_point: ""
  preview_only: false
  filename: ""
publishDate: 2018-03-01T00:00:00.000Z
url_poster: ""
url_code: ""
doi: ""
---
Product design (or the form of a product) is an important aspect of new product development. Using design patent data granted from 1977-2010, we categorized over 350,000 designs into over 9,000 styles (or categories of designs that are perceived to be visually similar).

Attached is the pseudocode if you wish to identify styles on a dataset of designs. If you use the data or would propose improvements / alternatives to our approach, please also let us know and we are happy to improve the approach over time, and acknowledge your work.



- - -

Given a similarity matrix between designs S

1. Select the group with the lowest conductance ϕ: Calculate e<sub>2</sub> from the second step of NJW (below) for each group of designs. Label the group with the smallest e<sub>2</sub> as G<sub>T</sub>. Label the corresponding e<sub>2</sub> as ϕ<sub>T</sub>. (Note that there is only one group in first iteration, so G<sub>T</sub>=G<sub>1</sub>).
2. Partition G<sub>T</sub> into two groups: Partition G<sub>T</sub> into two groups G<sub>T1</sub> and G<sub>T2</sub> using NJW. 
3. Evaluate if partitioning is to continue: measure conductance ϕ over all the groups that created thus far, and label the lowest value identified ϕ<sub>TNext</sub>. Stop if ϕ<sub>TNext</sub>>Δ+ϕ<sub>T</sub>. Else, repeat Steps 1-3. 


NJW<sup>1</sup>:
*	Compute the normalized graph Laplacian matrix L=I-D<sup>1/2</sup> SD<sup>1/2</sup> where I is the identity matrix and D is a diagonal matrix with each entry the degree of the vertex.
*	Compute the two smallest eigenvalues {e<sub>1</sub>,e<sub>2</sub>} and their associated eigenvectors {u<sub>1</sub>,u<sub>2</sub>} 
*	Let U∈R<sup>n×2</sup> be the matrix containing {u<sub>1</sub>,u<sub>2</sub>} as columns.
*	Normalize the rows of U to unit lengths (i.e., length = 1).
*	Treat every row as a point in space, and use K-means (two groups) to group the n data points.


<sup>1</sup>The approach relies on the Ng-Jordan-Weiss (2002) algorithm (NJW), which approximately partitions a group of objects into two groups by minimizing conductance (a graph measure of heterogeneity). The evaluate step stops the algorithm corresponding to a post-hoc identified Δ value of about 0.002, at which point a sharp increase in conductance is observed. (The NJW algorithm is popular and you can find ready implementations online, e.g., from [MATLAB central](https://www.mathworks.com/matlabcentral/fileexchange/44879-spectral-clustering)).

- - -
