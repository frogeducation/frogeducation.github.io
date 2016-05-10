---
layout: post
title:  "Intro to Frog's Automated Browser Tooling"
date:   2016-05-10 21:29:09 +0100
categories: automation dev
---

As Frog releases software a number of quality checks are performed to ensure the end product is up to scratch.  Checks include both manual and automated tests, this post provides an overview of our automated browser testing.  

#### So why do we implement implement automated browser testing?

**Reliable**: Most of the tests perform the similar operations every time they run; hence human errors can be eliminated.

**Repeatable**:  Software reaction can be tested under repeated execution.

**Programmable**:  Sophisticated tests can be programmed, which bring out the hidden information from the application.

**Comprehensive**: Building a suite of tests which covers every feature in the application is possible.

**Reusable**: The tests can be reusable on different versions of an application, even though the user interfaces changes.

**Better Quality Software**: More tests can run with few resources in less time, which ensures the quality of software better.

**Fast**: Like any automation, the automated tools to run tests are significantly faster than human testing.

#### What does our stack look like?

<img src="{{ site.baseurl }}/assets/tads-stack.gif" style="float:right;">

There are 2 primary components, the automation tooling for building a test and the environment to execute a test.

The foundation of our automation tooling is Selenium, an industry standard browser automation tool.  We trust Selenium to do its job and have utilised a Python based framework (TADS) to abstract Selenium complexities and simplify the development of our tests.

TADS is based on the Python based SST Framework https://pypi.python.org/pypi/sst/0.2.4, we have forked and evolved the framework for compatibility with Frog.

TADS defines a wide range of common actions such as login, create site, upload document, etc. which are then combined to build a test case.

<img src="{{ site.baseurl }}/assets/tads-hubs.png" style="float:right;">
