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
A randomized experiment using two or more variants of the same web page (A and B). Variant A is the original and variant B through n each contain at least one element that is modified from the original.

### Redirect test
A redirect test is a type of A/B test that allows us to test different web pages against each other. A redirect test contains different URLs for each variant. Redirect tests are useful when we want to test multiple different landing pages, or a complete redesign of a page.

### Multivariate test
Multivariate testing (MVT) helps us understand the interactions between multiple sections of a page by testing them together in a coordinated way. A multivariate test (MVT) tests variants of two or more portions of a web page simultaneously to see which combination creates the best outcome. Instead of showing which page variant is most effective (as in an A/B test), MVT identifies the most effective variant of each element and identifies the best combination of element variants.

For example, the multivariate test below is useful for identifying the best headline (H1 vs. H2) and hero image (A vs. B vs. C) combination to use on a landing page.
![Multivariate test](https://lh3.googleusercontent.com/GrfqjjtR68O6xbCt7olSnwSKVVM0bUzYPs7HXmXVbpDZNSqOBQR5mMPXwRUA1irb7A=w500)
