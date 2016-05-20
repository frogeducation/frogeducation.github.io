---
layout: post
title:  "Incident Notice - Manchester Data Center"
date:   2016-05-16 21:52:09 +0100
categories: in datacenter
---

A service notice regarding our Manchester Data Center Services

Status Update:
Datacentre Prolonged Downtime

Thursday 21st April 2016 1:14pm - 2:51pm

As part of our security policy we carried out an urgent upgrade to our core firewalls in the datacentre to bring them up to date with the latest firewall software and available security fixes.  This ensures that all our systems remain fully secure.  The impact of the vulnerability required an emergency change control.

The firewall updates had completed by 12:45pm and our tests confirmed everything to be online and working as expected. However due to our ISP’s router caches, we did not see any issues until 30 minutes after the updates had completed.

At 1:14pm we experienced a full outage of all central hosted services. Investigation into the issue by our team found a regression bug in the firewall software that caused the firewalls to lose some of its IP addresses, thus causing the outage.

This issue was fixed by our team at 2:45pm and all central services were back online by 2:51pm.

We have put in place a more stringent update and test procedure for our core firewall infrastructure to ensure any future incidents are avoided or downtime is kept to an absolute minimum. If our test procedure raises any issues or we have any concerns around a future update, we will formally arrange a maintenance window and send out communications ahead of time.

Frog has engaged with the core hosting team at our Manchester facility to ensure more transparency in the  upstream network configuration.

This has ensured the third party edge device configurations supporting Frog’s critical infrastructure is now aligned with our failover requirements.

This will ensure that issues such as those experienced on 21st April will not happen again.