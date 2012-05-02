demo-for-issue-19-in-hammerjs
=============================

issue #19 in hammer.js demo

Put this on your server and hit it with an iPad to see the problem (as compared to Chrome, Firefox, Safari).  The console includes a message whenever the hammer.js file hit the getXYfromEvent() function… this message fails to show up on the iPad when attempting a second toss of the same button (i.e., back to the bucket from which it came), but works in Chrome+.

There are other ways to test the bug in the appnd() function in the index.html page.


=============================
UPDATE: May 2 2012
=============================

The problem is not with Hammer.js, but rather with jQuery's append and appendTo functions.

In short, with an object like Hammer.js (and verified with another, similar javascript library), jQuery's append function won't work.  It will keep the events when it moves over, but lose track of the Hammer… i.e., events will no longer go through the Hammer to get hammered.  You can't simply add a new Hammer, because that seems to reactivate the old one and suddenly you have multiple Hammers, or something like that.  Very confused results ensue.

SOLUTION: 

I've posted a new file "fixed.html" here, where the appnd() function has the new code.  Instead of simply using jQuery's appendTo() alone, we first make a shallow clone() of the button (i.e., stripping the events), then we rebind the events one by one using the .data('events') from the original button, and finally we attach a new Hammer to the new button, and voila we have moved the button.

Cheers. 