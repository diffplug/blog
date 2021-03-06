# All of heartbleed

One of my pet peeves is when someone says "basically, the floober is flabbing", when the entire thing they're describing is just a flabbing floober. The "basically" implies that there's special knowledge that you'd need to be an expert to understand, but if they've actually told you the whole story, then it's leaving a false impression.

Here's a fantastic explanation of how Heartbleed works, by [xkcd](http://xkcd.com/1354/). Not "basically" how it works, this is exactly how the entire thing works.

If you're really curious, you can even look at the actual code that caused this whole kerfuffle:

[![Heartbleed Explanation](http://imgs.xkcd.com/comics/heartbleed_explanation.png)](http://xkcd.com/1354/)

Search for `memcpy(bp, pl, payload)` and you'll find the bug.

This is a command that copies `payload` number of bytes from `pl` (which is what the user sent - `POTATO`, `BIRD`, `HAT`, etc.) into `bp` (which is sent back to the user). But the programmer forgot to check whether payload matched the actual length of what the user sent in pl.  So when the user asks for 500 bytes of `HAT`, it will copy `HAT` for the first 3 bytes, and then whatever happens to be next in your computer's memory for the remaining 497. The real bug lets the user copy 64 thousand bytes at a time.

And that's why all your passwords are ruined now. Not basically why - all of why.

<!---freshmark follow
output = follow;
-->
[![Watch](https://img.shields.io/github/watchers/diffplug/blog.svg?style=social&label=Watch)](https://github.com/nedtwigg/blog/subscription)
[![Star](https://img.shields.io/github/stars/diffplug/blog.svg?style=social&label=Star)](https://github.com/nedtwigg/blog/stargazers)
[![Follow @NedTwigg](https://img.shields.io/twitter/follow/NedTwigg.svg?style=social&label=Follow)](https://twitter.com/NedTwigg)
[![Medium ned.twigg](https://img.shields.io/badge/Follow-41-blue.svg?style=social&logo=medium)](https://dev.to/nedtwigg)
[![dev.to nedtwigg](https://img.shields.io/badge/Follow-0-blue.svg?style=social&logo=dev.to)](https://dev.to/nedtwigg)
<!---freshmark /follow -->
