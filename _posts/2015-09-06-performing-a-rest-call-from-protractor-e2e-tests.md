---
id: 365
title: Performing a REST call from Protractor e2e tests
date: 2015-09-06T18:58:26+00:00
author: Gjermund Bjaanes
layout: post
guid: http://gjermundbjaanes.com/?p=365
permalink: /performing-a-rest-call-from-protractor-e2e-tests/
suevafree_template:
  - right-sidebar
dsq_thread_id:
  - 4104807803
categories:
  - CodeProject
tags:
  - Angular
  - Javascript
  - Programming
  - Testing
  - Web
---
I am currently trying to get some good end-to-end (e2e with protractor,  which is a great tool!)
 tests running for my Angular app ‘Extreme Results’.

I very quickly found a big problem. How do I clean up my database between tests and test-runs?

<!--more-->
The way I see it, there are two ways to solve this problem:

**1: Let the e2e tests actually clean up the way a user would.**

In other words, clicking around and deleting thing “manually” with tests.
Every test needs to manually clean up after themselves.
This actually works pretty well. It makes for a well tested application, but errors propagate quickly through every test.

**2: Calling the backend directly through REST between each test (or possibly between test “files”).**

This way, you can rely on tests being clean when you start with a new one.
Feels a bit safer and cleaner (and less error-prone).

&nbsp;

In my case, I was in no shape to even allow the user to delete stuff manually (not yet implemented in the app), so it made more sense to delete stuff through a REST call (also less work).

I use Parse as my back-end, so I created a Cloud Code function (which is just a REST call that fires some server-side code) that clears my entire database. Extremely dangerous code in other words. Do not deploy such code in production please!

If you want to see the Cloud Code, take a look on Github:
  
<a href="https://github.com/bjaanes/ExtremeResults-CloudCode/commit/e7452fce6701875fddfc5271d9083c31cc38e7fb" target="_blank">https://github.com/bjaanes/ExtremeResults-CloudCode/commit/e7452fce6701875fddfc5271d9083c31cc38e7fb</a>

&nbsp;

# Performing a REST call from your protractor tests

I created a common module that I can use from every test class. It looks like this:

<pre class="lang:js decode:true">var http = require('https');

var Common = function () {

    this.clearDB = function () {
        var deferred = protractor.promise.defer();

        var options = {
            hostname: 'api.parse.com',
            path: '/1/functions/clearDB',
            method: 'POST',
            headers: {
                'X-Parse-Application-Id': 'PARSE-APPLICATION-ID',
                'X-Parse-REST-API-Key': 'PARSE-REST-API-KEY'
            }
        };

        var callback = function() {
            deferred.fulfill();
        };

        var req = http.request(options, callback);
        req.end();

        return deferred.promise;
    };

};

module.exports = Common;</pre>

It uses a node package called https.

I set up some options like host, path, method and headers.

And then I just perform the call with _http.request()_ and _req.end()_. Simple and nice.

They way I actually use this is even simpler:

<pre class="lang:js decode:true">var OverviewPage = require('./overview.po.js');
var Common = require('../common/common.js');

describe('Overview Page', function () {

    var overviewPage = new OverviewPage();
    var common = new Common();

    beforeAll(function () {
       common.clearDB();
    });

    // Tests...

});</pre>

The important bits are:

<pre class="lang:js decode:true">var Common = require('../common/common.js');</pre>

<pre class="lang:js decode:true"><span class="pl-k">var</span> common <span class="pl-k">=</span> <span class="pl-k">new</span> <span class="pl-en">Common</span>();</pre>

Which both set up the required &#8216;common' module.

But the real code is:

<pre class="lang:js decode:true ">beforeAll(function () {
       common.clearDB();
 });
</pre>

Which actually performs the database clear between every tests. Nice!