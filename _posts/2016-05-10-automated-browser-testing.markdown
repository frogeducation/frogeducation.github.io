---
layout: post
title:  "Intro to Frog's Automated Browser Tooling"
date:   2016-05-10 21:29:09 +0100
categories: automation dev
---

As Frog releases software a number of quality checks are performed to ensure the end product is up to scratch.  Checks include both manual and automated tests, this post provides an overview of our automated browser testing.  

#### Why do we implement implement automated browser testing?

**Real World UX**: Automated browsers are closest to a 'real world' experience. They highlight gaps in our other test tooling by acting like a human. 

**Reliable**: Most of the tests perform the similar operations every time they run;  human errors can be eliminated.

**Repeatable**:  Software reaction can be tested under repeated execution.

**Programmable**:  Sophisticated tests can be programmed, which bring out the hidden information from the application.

**Comprehensive**: Building a suite of tests which covers every feature in the application is a possibility.

**Reusable**: The tests can be reusable on different versions of an application, even though the user interfaces changes.

**Better Quality Software**: More tests can run with few resources in less time, which ensures the quality of software better.

**Fast**: Like any automation, the automated tools to run tests are significantly faster than human testing.

#### What does our stack look like?

<img src="{{ site.baseurl }}/assets/tads-stack.gif" style="float:right;">

There are 2 primary components, the automation tooling for building a test and the environment to execute a test.

The foundation of our automation platform is Selenium, an industry standard browser automation tool.  We trust Selenium to do its job and have utilised a Python based framework (TADS) to abstract Selenium complexities and simplify the development of our tests.

TADS is based on a Python framework called SST, we have forked and evolved the framework for compatibility with Frog. SST keeps things simple, tests are made up of scripts, created by composing actions that drive a browser and assert conditions. We have the flexibility of the full Python language, along with a convenient set of functions to simplify web testing.

TADS also defines a wide range of common Frog actions such as login, create site, upload document, etc. which are then combined to build a test case.

#### How do we execute tests?

This part evolved from simple to complicated fast.  The simplest method of test execution is via a local copy of the selenium/TADS environment, this is great when building tests or playing with ad-hoc runs but the value of automation is execution at scale (multiple browsers, operating systems etc.).  This requires a myriad of environments but key to that is the Selenium Grid. Selenium-Grid allows you run your tests on different machines against different browsers in parallel. 'Nodes' are added to the grid allowing the 'hub' to organise the most efficient way to execute the tests.  

We currently have ~150 active browsers at any one time in two environments:

- our 'clean' VM environment in BrowserStack and our in-house developed headless cluster. 'Clean' because they spin up a brand new VM for each test.
- our 'dirty' environment made up of commodity hardware (windows, macs, Firefox, Chrome, etc.). 'Dirty' because we treat them as a user would, some are updated, some not, some store cache, some don't - you get the idea.

<img src="{{ site.baseurl }}/assets/tads-hubs.png" style="float:right;">

#### What does all this get us?

We have a 4-5 hours manual test across every major feature fully scripted and running against a number of working and release branches, this allows us identify any significant defect pretty quickly. It has significant value in highlighting challenges with long and disparate user journeys that are difficult to realise elsewhere as well as the catching subtle differences between browsers and operating systems.

Automated browser testing fits alongside a number of other tools available to us but in terms of projecting confidence in our product it's by far the most effective.  Everyone in the business understands a browser replaying actions like a user on a screen they can watch, they are less confident about a unit test that was executed 'magically' producing a green blob on a screen buried in dev.


