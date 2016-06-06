---
layout: post
title: Incident Notice - I Am Learning
date: '2016-05-20 20:31:27 +0100'
categories: in datacenter
---

A service notice regarding I Am Learning services

Status Update: I Am Learning service outage

Thursday 17th May 2016 7:30pm - 9:27pm

During the afternoon of Thursday 17th of May, the Frog monitoring system determined an issue with inode exhaustion on the primary web server, holding user content. Removal of superfluous log files and cache items ensured services continued running.

Emergency maintenance was then scheduled to further reduce inode usage across the web cluster. Upon completion, a rolling restart of services occurred. Monitoring reported complete service restoration.

At 8.45pm management alerted the on call team that services were not functioning as expected. It was determined that a failover IP, allocated to supporting MySQL services had dropped out of the cluster pool. Detailed investigation suggests that this was an isolated anomaly due to an issue with manual configuration; and not cause for future concern.

This issue was rectified by our team at 9:25pm and all central services were back online by 9:27pm.

A complete review of the Frog monitoring system occurred the following morning. This showed that while front end services are adequately monitored, a full application check, ensuring MySQL is returning known results did not align to service expectations.

Further stringent checks and notifications are now in place to ensure service integrity is maintained across the I Am Learning estate.
