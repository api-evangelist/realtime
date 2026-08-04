---
title: "LiveObjects comes to Java: navigating shared state with the path API"
url: "https://ably.com/blog/liveobjects-java-path-api"
date: "2026-07-20"
author: "Evgenii Khokhlov"
feed_url: "https://voltaire.ably.com/blog/rss.xml"
---
LiveObjects now supports Java, and the path-based model that reshaped the JavaScript API is built in from the start. Instead of holding a reference to a specific object, PathObject lets you point at a location in the tree, so a reference keeps working even after the object underneath gets replaced.
