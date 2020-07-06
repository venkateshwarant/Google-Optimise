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

2. Google Analytics installed on our product website.
* A detailed procedure to install Google Analytics in the helloworld product is given in [Getting started section.](##Getting-started)

3. The Chrome web browser.
* To create experiment variants with the visual editor, we need Google Chrome with the Optimize extension

4. Optional: Optimize Chrome extension to create experiences in the Optimize visual editor. The Chrome extension isn't required to view reports.
* Get it installed in the browser from this [link](https://chrome.google.com/webstore/detail/google-optimize/bhdplaindhdkiflmbfbciehdccfhegci)


## Basic terminologies
### A/B test
A randomized experiment using two or more variants of the same web page (A and B). Variant A is the original and variant B through n each contain at least one element that is modified from the original. The test is run mainly to determine which variant is popular among the users. We can assign weight to each variant. This weight is the probability that a random user will get the particular variant. Even we can target some variant to some geographical location. There are other multiple criteria for targeting which we will look in later sections.

### Redirect test
A redirect test, (a.k.a. split URL test), is a type of A/B test that allows us to test separate web pages against each other. In redirect tests variants are identified by URL or path instead of an element(s) on the page. Redirect tests are useful when we want to test two very different landing pages, or a complete redesign of a page.

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

## Getting started

Google Analytics is a service offered by Google to implement tracking code, and set up data filters. With this service we can analyze our product's Audience, Acquisition, and Behavior reports, and set up goals and campaign tracking. Google Optimize is built as a separate serice which we can integrate with Google Analytics to create experiments with different ways of delivering the website content.

**Steps to configure Google Optimize is as follows**:

1. Follow this [link](https://support.google.com/analytics/answer/1008015?hl=en) to create an account in Google Analytics. Create a web property named "helloworld" in the Analytics account. A property represents the website or an app, and is the collection point in Analytics for the data from the site or app.

2. After creating the property, goto Admin > Account User Management > Permissions > enable all the permissions (Edit, Collaborate, Read&Analyse, Manage Users)

3. Goto Admin > PROPERTY column > Tracking Info > Tracking Code. The Tracking ID is displayed at the top of the page. The global site tag is displayed farther down the page in a text box under Website Tracking > Global Site Tag (gtrag.js)

**The global site tag**:
The global site tag is several lines of code that we need to paste into each webpage we want to measure. It is similar to the below lines of code:
```
 	 <!-- Global site tag (gtag.js) - Google Analytics -->
	<script async src="https://www.googletagmanager.com/gtag/js?id=UA-xxxxxxxxx-x"></script>
	<script>
	  window.dataLayer = window.dataLayer || [];
	  function gtag(){dataLayer.push(arguments);}
	  gtag('js', new Date());
	
	  gtag('config', 'UA-xxxxxxxxx-x');
	</script>
```

**NOTE**:
**Tracking ID and property number**:
* The tracking ID is a string like UA-000000-2. It must be included in the tracking code to tell Analytics which account and property to send data to.
* The first set of numbers (-000000, in the example above) refers to the analytics account number, and the second set of numbers (-2) refers to the specific property number associated with the account.

4. Add those lines of code immediately after the ```<head>``` tag on each page which we have to track.
  
5. We have to verify that our global site tag is working. To verify that the tag is working, visit our product website, and then check the [Real-Time reports](https://support.google.com/analytics/answer/1638635) in Analytics to verify that our visit was registered.

6. Follow this [link](https://support.google.com/optimize/answer/6211921) to setup an Optimize account.
