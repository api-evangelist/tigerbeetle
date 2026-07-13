---
title: "Swarm Testing Data Structures"
url: "https://tigerbeetle.com/blog/2025-04-23-swarm-testing-data-structures"
date: "2025-04-23"
author: "matklad"
feed_url: "https://tigerbeetle.com/blog/atom.xml"
---
We discovered a cute little pattern the other day when refactoring TigerBeetle’s intrusive queue — using Zig’s comptime reflection for exhaustively testing data structure’s public API. Isn’t it cool when your property test fails when you add a new API, because “public API is tested” is one of the properties you test?!
