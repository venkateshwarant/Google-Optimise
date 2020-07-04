# Google-Optimize
A guide to setup AB testing using Google-Optimise

## General overview
This tutorial shows how to setup Google-Optimise and run AB tests in [Web-based Hello World case study](https://github.com/acapozucca/helloworld).

## Assumptions/Pre-requisites

### Hardware
Laptop with at least 8 Gb memory (recommended 16 Gb, ideally 32 Gb)

### Software

1. The Web-based Hello World case study
* Instructions to install here: https://github.com/acapozucca/helloworld/blob/master/product.helloworld/README.md
* The product has to be deployed and tested whether it is available

## Basic terminologies
### A/B test
A randomized experiment using two or more variants of the same web page (A and B). Variant A is the original and variant B through n each contain at least one element that is modified from the original. The test is run mainly to determine which variant is popular among the users. We can assign weight to each variant. This weight is the probability that a random user will get the particular variant. Even we can target some variant to some geographical location. There are other multiple criterias for targetting which we will look in later sections.

### Redirect test
A redirect test, (a.k.a. split URL test), is a type of A/B test that allows you to test separate web pages against each other. In redirect tests variants are identified by URL or path instead of an element(s) on the page. Redirect tests are useful when you want to test two very different landing pages, or a complete redesign of a page.

![Redirect test](https://lh3.googleusercontent.com/_GrZ6NO0PPKTJ6UME2MGZyUV_YRZM-YcbGqA6u4dT6nKwX1zom5Msrp3jIDm9Zzzzmw=w300)

Example
Test two different landing pages, with different URLs:

Original – www.example.com/landing1
Variant – www.example.com/landing2
Test a redesigned page hosted on a subdomain:

Original – www.example.com
Variant – new.example.com

### Multivariate test
Multivariate testing (MVT) helps us understand the interactions between multiple sections of a page by testing them together in a coordinated way. A multivariate test (MVT) tests variants of two or more portions of a web page simultaneously to see which combination creates the best outcome. Instead of showing which page variant is most effective (as in an A/B test), MVT identifies the most effective variant of each element and identifies the best combination of element variants.

For example, the multivariate test below is useful for identifying the best headline (H1 vs. H2) and hero image (A vs. B vs. C) combination to use on a landing page.

![Multivariate test](https://lh3.googleusercontent.com/GrfqjjtR68O6xbCt7olSnwSKVVM0bUzYPs7HXmXVbpDZNSqOBQR5mMPXwRUA1irb7A=w500)
