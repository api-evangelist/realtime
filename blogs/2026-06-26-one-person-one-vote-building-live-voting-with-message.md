---
title: "One person, one vote: building live voting with message annotations"
url: "https://ably.com/blog/one-person-one-vote-building-live-voting-with-message-annotations"
date: "2026-06-26"
author: "Simon Woolf"
feed_url: "https://voltaire.ably.com/blog/rss.xml"
---
Live polls are a staple of conferences, streams, and all-hands: a question goes up on the big screen, everyone votes from their phone, and the bars race each other in realtime. There's a lot of different ways you could implement this. The most obvious way is a CRUD app backed by a server that votes are POSTed to, and the server keeps a running count.
