---
title: "Snapshot Testing For the Masses"
url: "https://tigerbeetle.com/blog/2024-05-14-snapshot-testing-for-the-masses"
date: "2024-05-14"
author: "matklad"
feed_url: "https://tigerbeetle.com/blog/atom.xml"
---
Snapshot testing is a technique for the “assert” part of an “arrange, act, assert” test, that dispenses with hand-written assertions, and instead uses comparison to a known good value, a snapshot. Crucially, in the case of a mismatch, a snapshot can update itself. A video is worth a thousand words:
