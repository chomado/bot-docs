---
title: Embedding a bot in a website | Microsoft Docs
description: Learn how to design a conversational application (bot) that is embedded within a website.
keywords: bot framework, design, bot, scenario, use case, pattern, bot in website, backchannel, web chat control, Skype web control
author: matvelloso
manager: rstand
ms.topic: design-patterns-article
ms.prod: bot-framework

ms.date: 
ms.reviewer: rstand
#ROBOTS: Index
---
# Embedding bots in websites


Although bots commonly exist outside of websites, they can also be embedded within a website. 
For example, you may embed a [knowledge bot](~/design/patterns-knowledge-base.md) within a website 
to enable users to quickly find information that might otherwise be challenging to locate within complex website structures. 
Or you might embed a bot within a help desk website to act as the first responder to incoming user requests. 
The bot could independently resolve simple issues and [handoff](~/design/patterns-human-handoff.md) more complex issues to a human agent. 

This article explores integrating bots with websites and 
 the process of using the `backchannel` mechanism to facilitate private communication between a web page and a bot. 

Microsoft provides two different ways to integrate a bot in a website: 
the Skype web control and an open source web control.

## Skype web control

The Skype web control is essentially a Skype client in a web-enabled control. Built-in Skype authentication enables the bot to authenticate and recogize users, without requiring the 
developer to write any custom code. Skype will automatically recognize Microsoft Accounts used in its web client. 

Because the Skype web control simply acts as a front-end for Skype, 
the user's Skype client automatically has access to the full context of any conversation that the web control facilitates. 
Even after the web browser is closed, the user may continue to interact with the bot using the Skype client. 

## Open source web control

The <a href="https://github.com/Microsoft/BotFramework-WebChat" target="_blank">open source web chat control</a> 
is based upon ReactJS and uses the 
[Direct Line API](https://docs.botframework.com/en-us/restapi/DirectLine3/#navtitle) 
to communicate with the Bot Framework. The web chat control provides a blank canvas for implementing the web chat, 
giving you full control over its behaviors and the user experience that it delivers. 

The `backchannel` mechanism enables the web page that is hosting the control 
to communicate directly with the bot in a manner that is entirely invisible to the user. 
This capability enables a number of useful scenarios: 

- The web page can send relevant data to the bot (e.g., GPS location).
- The web page can advise the bot about user actions (e.g., "user just selected Option A from the dropdown").
- The web page can send the bot the auth token for a logged-in user.
- The bot can send relevant data to the web page (e.g., current value of user's portfolio).
- The bot can send "commands" to the web page (e.g., change background color).

## Using the backchannel mechanism

[!include[Introduction to backchannel mechanism](~/includes/snippet-backchannel.md)]

## Additional resources

- <a href="https://docs.botframework.com/en-us/restapi/DirectLine3/#navtitle" target="_blank">Direct Line API</a>
- [Activity types](~/dotnet/activities.md)
- [Use the backchannel mechanism](~/nodejs/backchannel.md)

<!--
This article covered ways to integrate bots with websites and 
explored the process of using the `backchannel` mechanism to facilitate private communication between web page and bot. 
For a detailed walk through of how to use the backchannel mechanism with the 
open source web chat control with Node.js, see [Use the backchannel mechanism](~/nodejs/backchannel.md). 
-->