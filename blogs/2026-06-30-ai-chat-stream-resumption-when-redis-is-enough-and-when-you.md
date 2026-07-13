---
title: "AI chat stream resumption: when Redis is enough, and when you need durable sessions"
url: "https://ably.com/blog/ai-chat-stream-resumption"
date: "2026-06-30"
author: "Madeleine Quinn"
feed_url: "https://voltaire.ably.com/blog/rss.xml"
---
The Redis approach to AI chat stream resumption works for page reloads. It runs into trouble with multi-device, enterprise networks, and the cost of writing every token. Here's when each transport-layer choice fits.
