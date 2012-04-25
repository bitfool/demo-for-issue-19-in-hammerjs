demo-for-issue-19-in-hammerjs
=============================

issue #19 in hammer.js demo

Put this on your server and hit it with an iPad to see the problem (as compared to Chrome, Firefox, Safari).  The console includes a message whenever the hammer.js file hit the getXYfromEvent() function… this message fails to show up on the iPad when attempting a second toss of the same button (i.e., back to the bucket from which it came), but works in Chrome+.

There are other ways to test the bug in the appnd() function in the index.html page.