---
title: The Need for Secure Text Communication
layout: post
tags: ["personal"]
---

Every human being has a right to privacy, given that we spend most of our lives online, maintaining that privacy in the digital world becomes even more important. The argument that one has to choose between privacy and security in a free world is inherently flawed. We cannot forget that privacy is freedom and a society that values security over privacy is not free at all.

<!--excerpt-->

Governments across the world argue that it is only the metadata, not the content they collect to protect the citizens from the threat of terrorism although we now know that it is a [lie](http://www.theguardian.com/world/2013/jul/31/nsa-top-secret-program-online-data). Then we have the companies that provide the so called _free_ services where the user is the product and the content they generate is another [data point](https://support.google.com/mail/answer/6603?hl=en) that these companies [distribute](http://arstechnica.com/tech-policy/2010/05/latest-facebook-blunder-secret-data-sharing-with-advertisers/) for profit. 

Amidst [inane calls](http://www.washingtonpost.com/blogs/the-switch/wp/2015/06/04/fbi-official-companies-should-help-us-prevent-encryption-above-all-else/) for compromise on security from government agencies that neither comprehend nor see the possible consequences of [such actions](http://www.washingtonpost.com/world/national-security/chinese-hackers-breach-federal-governments-personnel-office/2015/06/04/889c0e52-0af7-11e5-95fd-d580f1c5d44e_story.html) the responsiblity of protecting one's privacy falls on the individuals and the tech community. The tech community has been [vocal](http://techcrunch.com/2015/06/02/apples-tim-cook-delivers-blistering-speech-on-encryption-privacy/#.s4ng9g:nsp4) in it's efforts to protect these freedoms but it has fallen short in one major aspect; **Text communication**.

The tech community chose usability over security when it first built applications for Email and Instant Messaging which is one of the reasons for such a large scale adoption of these practices. The truly secure [applications](https://emailselfdefense.fsf.org/en/) are found wanting in user experience. Nevertheless, efforts are being made by the community to make these applications accessible to the masses. As my contribution to this, I built a simple javascript application [Fumble Text](https://arelangi.github.io/Fumble-Text) that lets anyone encrypt/decrypt text and share it over unsecure channels, provided that the communicating parties have shared a secret key/passphrase over a secure channel, that let's them decrypt the text. The application is possible because of the open source community, I simply combined two excellent libraries, [CryptoJS](https://code.google.com/p/crypto-js/) and [zxcvbn](https://github.com/dropbox/zxcvbn).

> "We must be free not because we claim freedom, but because we practice it."
	~ William Faulkner