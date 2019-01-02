---
date: 2019-01-01
linktitle: How does bell synchronize? 
title: How does bell synchronize?
---
As the first of the (hopefully) monthly posts, let's talk about one of the earliest "discoveries" I made when I first made bell: the school bell is not actually on time (usually).

Most of the time, the school bell is only a couple of seconds off of the correct time, so not many people noticed until I made the bell website. ([It has been much farther off from correct before](https://web.archive.org/web/20190102010620/https://lahstalon.org/for-the-two-and-a-half-weeks-los-altos-bells-have-been-two-minutes-early/).) 

One of the first complaints I received when making the bell website was that the website wasn't perfectly correct. People would be disappointed if, for example, the website said 0:02 when the bell rings. But the problem wasn't just the school's time. Some friends also showed me that their devices were several minutes off.

There was a second problem here: each person's device might have a slightly different time. The solution? Synchronize everyone to the bell website's own time, and then from there create an adjustment for the school bell.

To do this, I initially implemented my own time synchronization algorithm, which worked but was kind of slow. It turns out that there is a package called [timesync](https://www.npmjs.com/package/timesync) which does exactly this, so that is what bell.plus uses as of the time of writing this post. The school correction was actually slightly harder to solve, because I observed it would vary from day to day. Since I made bell.lahs.club when I was a senior and still attending the school everyday, I created a bot on the Telegram messenger that I could send commands during the passing periods to synchronize the bell each day if it was off. For example, if the bell rang one second before the website said it would, I would send the message "bellAdd 1000" to push the website forward 1000 milliseconds (= 1 second). Currently, since I'm at college now, the LAHS Hack Club helps set the day to day corrections. You can actually see [the raw correction](https://bell.plus/api/data/lahs/correction) if you're interested...

I hope this was a somewhat interesting post! 
