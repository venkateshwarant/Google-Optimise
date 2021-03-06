# Google-Optimize
A guide to setup AB testing using Google-Optimise

## General overview
This tutorial shows how to setup Google-Optimise and run AB tests in [Web-based Hello World case study](https://github.com/acapozucca/helloworld).

## Assumptions/Pre-requisites

### Hardware
Laptop with at least 8 Gb memory (recommended 16 Gb, ideally 32 Gb)

### Software

1. **The Web-based Hello World case study**
* Instructions to install here: https://github.com/acapozucca/helloworld/blob/master/product.helloworld/README.md
* The product has to be deployed and tested whether it is available

2. **Google Analytics installed on our product website.**
* A detailed procedure to install Google Analytics in the helloworld product is given in steps 1-5 in [Getting started section.](#getting-started)

3. **The Chrome web browser.**
* To create experiment variants with the visual editor, we need Google Chrome with the Optimize extension

4. **Optional: Optimize Chrome extension** to create experiences in the Optimize visual editor. The Chrome extension isn't required to view reports.
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

### Experiences
Experiences are website customizations made to achieve a desired goal. These customizations can be simple (e.g. a new Call To Action (CTA), or a larger thumbnail photo) or complex (e.g. multivariate and redirect tests)

A common goal for website publishers is to produce better user experiences. Better user experiences increase brand trust, which creates loyal customers, which increases sales. Another common goal is to create personalized experiences that increase loyalty, stickiness and average cart size.

In Optimize, experiences can either be tests (e.g. A/B, redirect, or MVT) or personalizations.

### Tests
A test consists of variants of our web page that we wish to measure against our original page to determine which is most effective at achieving our objective. Examples include A/B, redirect, and multivariate tests. Tests are measured based on the objective(s) we specify and can run for a maximum of 90 days.

### Personalizations
Personalizations are a set of changes that we can target to a specific set of users. Unlike tests, personalizations can run forever and do not have variants - we have one set of changes that are shown to everyone who meets the targeting conditions.

### Section
A section is a single element of a web page (e.g. a button or an image) that is modified to create variants. An A/B test contains one section (with one or more variants). In a multivariate test, multiple sections are tested at the same time (e.g. a button and an image).
## Getting started

Google Analytics is a service offered by Google to implement tracking code, and set up data filters. With this service we can analyze our product's Audience, Acquisition, and Behavior reports, and set up goals and campaign tracking. Google Optimize is built as a separate serice which we can integrate with Google Analytics to create experiments with different ways of delivering the website content.

**Steps to configure Google Optimize:**

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

6. Follow this [link](https://support.google.com/optimize/answer/6211921) to create and setup an Optimize account.

7. Link the Optimize account to the corresponding Analytics property(Follow the above link for this).

8. We should install [Optimize chrome extension](https://chrome.google.com/webstore/detail/google-optimize/bhdplaindhdkiflmbfbciehdccfhegci) to edit our web pages with their visual editor feature. This feature comes in handy to edit web pages on the go.

Now that we have configured and installed Google Optimize in our web page, we can see how to create tests and use different types of targettings.

## Creating testcases

### Creating AB Testcase

1. Goto the Optimize account. Then click on the containers name to goto the experiments page. Then click Create experiment.

2. Enter an Experiment name (up to 255 characters).

3. Enter an Editor page URL (the web page we like to test).

4. Click A/B test. Then click Create

![Create test](https://lh3.googleusercontent.com/kjoxLrZ-5Tk3GTS_oxSd_h7gB4VfS9MNsJ-ctejJWlFtoOWZMyDS244IGuOXSnwUNDtj=w895)

#### Variants

Normally AB test consists of 2 different variants. Here, we can create multiple variants of the test webpage. This is known as A/B/n Testing. To create a variant, click Create Variant, enter a variant name, then click Add. To start making changes. click anywhere in the variant row (which will say "0 changes"). This will launch the Optimize visual editor. Start editing in the visual editor and save it. All variants are weighted equally by default in Optimize. A visitor who is included in our experiment has an equal chance of seeing any of our variants. If we want to direct more, less, or even all of our traffic to a specific variant, we can adjust your variant weights on the experiment details page.

#### Objectives
There are three predefined objectives. They are-
1. **Pageviews**
It is the number of total views the corresponding webpage has got. Repeated views of a single page are counted.
2. **Session duration**
The length of a session in seconds. A session lasts as long as there is continued activity.
3. **Bounces**
Bounces are the number of single-page visits.

### Creating Multivariate Testcase

1. Creating a multivariate testcase is same as that of [creating AB testcases](#creating-ab-testcase) except that in the final step we have to choose Multivariate test.

2. Once the multivariate test is created, we have to create multiple options for each sections.
NOTE: Refer [section](#section) to know more about sections.

3. Once multiple options for sections is done, Optimize automatically creates the different combinations of the sections.

4. We can select the objective and can target the test to a particular type of customer.

### Creating Redirect Testcase

1. Creating a redirect testcase is same as that of [creating AB testcases](#creating-ab-testcase) except that in the final step we have to choose redirect test.

2. Optimize supports two types of redirect tests, single page and advanced.
**Redirect to a single page** – Redirect pages to a single web page (with one or more variants) by specifying a URL.
**Advanced redirect** – Modify part of the editor/original URL, redirect to multiple pages, and use regex.

3. Once redirect test is created, we have to create variants of the URL. With this redirect test we can redirect the network calls made to a URL to another URL.


## Targettings
This feature is used to target a test or a personalisation to a certain set of customers. Optimize includes two controls for targeting: Who and When. Who determines whether a user is eligible to be included in an experiment. When determines when it is appropriate to serve an eligible user (see Who, above) with an experiment variant. It is mandatory to configure who and when conditions while setting-up the targetting.

### Google Analytics audiences
This is an Optimize 360 feature (Optimize 360 is a paid suite provided Google).This allows us to focus our experiment on a group of users who have exhibited specific behaviors on our site. Audience targeting is useful for targeting high-value customers with special offers and incentives or loyal customers with an email signup. We can target users interested in a specific product category to see if a customized home page increases conversions. 

### Google Ads
To use this feature, we have to configure the Google Ads account. To configure Google Ads we need to have a proper website, so we cannot test it in localhost. This allows us to personalize our existing web pages based on specific ads that users click. For example, say if the user has already clicked ads related to shoes. Then we can personalize for that user to show products and deals related to shoes in our ecommerce website. 


