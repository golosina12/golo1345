---
title: DuckDuckGo Smarter Encryption
nav_title: Smarter Encryption
description: DuckDuckGo never tracks you. And when you leave our search engine and use our apps or extensions to browse other sites, we aim to protect your privacy as much as possible.
category: Web Browsing Privacy
order: 200
---

At DuckDuckGo, we don’t track you, ever. That’s our [privacy policy](https://duckduckgo.com/privacy) in a nutshell. For example, we do not create unique cookies and, more generally, architect our product so that we do not even have the ability to create a search or browsing history for any individual — it’s privacy by design.

We believe getting the privacy you deserve should be as easy as closing the blinds, and we make privacy protection tools to help you seamlessly control your personal information online. These tools include the [DuckDuckGo Privacy Essentials](https://duckduckgo.com/app) browser extension for Firefox, Chrome and Safari, as well as the [DuckDuckGo Privacy Browser](https://duckduckgo.com/app) app for iOS and Android. They each contain several leading privacy technologies we've developed to reduce your digital footprint, such as DuckDuckGo Search, Tracker Blocking, and Smarter Encryption.

This explanation is about our Smarter Encryption technology, and in particular network requests you may notice going to smarter_encryption.js from our apps and extensions. This technology is used to determine if a website can be upgraded to an encrypted version, both without breaking your browsing experience and completely protecting your privacy.

With Smarter Encryption, your browsing will use encrypted connections more often. That means fewer prying eyes on your browsing history, like from your Internet provider or wi-fi snoopers. The way it works is we continually maintain a list of sites that support encryption. When you try to go to an unencrypted site that we know supports encryption (i.e. is on our list), we first automatically upgrade your connection to use the encrypted version of the website. It's seamless!

Our Smarter Encryption list is quite large: over 10 million sites and growing. Due to this large size, the list cannot be fully stored in the apps or extensions installed on your devices. Instead, we store the most trafficked sites locally on your devices, and keep the rest of the list on our servers.

Here's how it works:

1.  You click or navigate to an insecure (http) domain such as http://spreadprivacy.com
2.  The spreadprivacy.com domain would first be looked up in your local list (the one on the device with the most trafficked sites) to see if it can be upgraded immediately.
3.  If not, it will be converted to a SHA-1 hash: 194a8d7aa538455b8c3a2ff68dcd3a4c5d80743a (see https://en.wikipedia.org/wiki/Hash\_function & https://en.wikipedia.org/wiki/SHA-1 for more details on how that conversion works)
4.  The first four characters of this hash (194a) are sent to our anonymous smarter_encryption.js service. Our logs never contain IP addresses or other personal information, so just like anonymous queries on [DuckDuckGo Search](https://duckduckgo.com), we do not know anything about who is making these requests. Only you and your device know. Nevertheless, we added another layer of privacy protection to this anonymous service by only having your device send the first four characters of the hashed domain, such that in any case the service cannot tell what exact domain you are visiting.
5.  The anonymous service sends back any hashed domains from the full Smarter Encryption list that match the first four characters of the hash sent (e.g. https://duckduckgo.com/smarter\_encryption.js?pv1=194a). It's possible that it will send back nothing (if nothing matches).
6.  Your device looks through the returned hashed domains to see if the hash of the domain you are visiting exactly matches one of hashed domains returned. If so, it is upgraded!

**To be clear, this means that your searches and browsing history are still completely anonymous.**

If you have any concerns, please feel free to <a href="{{ site.baseurl }}/company/contact-us/">contact us</a>, or join the discussion in the [DuckDuckGo subreddit](https://reddit.com/r/duckduckgo).
