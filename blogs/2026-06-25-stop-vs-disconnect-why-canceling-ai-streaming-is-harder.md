---
title: "Stop vs disconnect - why canceling AI streaming is harder than it looks"
url: "https://ably.com/blog/stop-vs-disconnect-canceling-ai-streaming"
date: "2026-06-25"
author: "Madeleine Quinn"
feed_url: "https://voltaire.ably.com/blog/rss.xml"
---
Clicking stop closes the HTTP connection, not the underlying generation. This is documented Vercel AI SDK behavior. Here's why it matters and what a correct stop implementation actually requires.
