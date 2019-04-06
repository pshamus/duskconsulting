---
title: Automating the seemingly impossible
subtitle: How PowerShell enabled fully automatic configuration of the BizTalk ESB Toolkit
date: 2019-04-06
draft: true
tags: ["Automation", "BizTalk", "PowerShell"]
---

There are very few problems I couldn't solve with PowerShell. Then one day I needed to fully automate a BizTalk 2016 infrastructure, complete with an app server and two separate SQL servers for the Message Box and other system databases, respectively. No sweat, I thought. Sure it would be challenging but I'm always up for a good challenge.

As I progressed, I was able to find the methods of silent installation and configuration for the SSO Master Secret Server, BizTalk itself, and the adapter packs. A few configuration files with the proper settings and boom, everything came together nicely. Next step: ESB Toolkit.

After some initial investigation, I was able to find the right silent install command options. Great, I thought, I'm making great progress. The only part left was to perform the automated configuration. Surely there had to be a way like the main BizTalk installer had.

Nope.

The ESB Toolkit is a simple Windows .NET Forms app that allows for easy configuration of its settings, which are stored in the file '' located in the installation directory. After trying every possible combination of command line switches I could think of and getting no feedback (like a list of parameters and their values), I resorted to using PowerShell and reflection to see just what was going on.



Poking around in the innards of a .NET application is not for the faint of heart. It was both frustrating and very time consuming.