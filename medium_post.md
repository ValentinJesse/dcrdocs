
# Flotorizer: An experiment on Blockchain for noobs.



Let me preface this post by letting you know that I am not a developer, the only class related to programming that I ever took was 15 years ago, in Pascal — that’s right, Pascal. I am a [scientist](https://scholar.google.com/citations?user=ZiSXc5AAAAAJ&hl=en) and I learned how to program Python with friends, colleagues, the internet (thanks StackOverflow). My programming self-education was mostly oriented by challenges related to [bioinformatics](http://www.pnas.org/content/114/48/12809.abstract) and scripting tools to analyze atomic trajectories of [molecular dynamics simulations](https://www.nature.com/articles/ncomms3881). 

All that to say that you don’t need to know much about blockchain to make an app with [Flotorizer](http://flotorizer.net). Why not? Because [Alexandria API](https://api.alexandria.io/docs/) is a thing.

### The beginnings

I started to learn Node.js about two years ago — not full time, I am a scientist remember? — because bioinformatics applications are much more fun (and useful) if they are interactive, and on the web *so you can brag about it by sharing a link*. I went to one of those [NodeTogether](http://www.nodetogether.org/) seminar given by [ashley williams](undefined) and learned enough to really get me going with Node.js. (Thanks [ashley](undefined)). 

I also had a very good friend, Luke Ulrich, who knows a lot of javascript and were working on a project with me… anyways… two years in and I am embarrassed to say that I am still fumbling around with concepts such as promises and callbacks — fun huh?

Anyways, when I started to check out the then florincoin ecosystem, I barely knew what a blockchain was, but I knew that this tx_comment feature was very interesting. Wait… can I just write whatever I want on the **blockchain** of an ongoing cryptocurrency? How do I do that?

My curiosity took me to [Alexandria](http://alexandria.io), where I registered and felt tempted to upload [an album](https://alexandria.io/browser/ed6474) that I had recorded with some friends back in Tennessee, it did not work the first few times but it finally went through. In the process, I met [Devon Read](undefined), the CEO of Alexandria himself and my first contact in the FLO community. I met him because I entered on [their chat channel](https://chat.alexandria.io/) and started asking questions.

At this point, I only had a vague idea of how cryptocurrencies worked: I need to have an address… but where is the address stored? What is wallet? What is paper wallet? What happens to this address that I just made but will never use?

Anyhow… after reading some blogs and wikis I later realized that Alexandria made me a wallet when I registered (thank you Alexandria) and also gave me an address. Cool, now I have a wallet, an address, how can I write on the blockchain?
> # To write in the FLO blockchain you just need to make a transaction. — [Joseph Fiscella](undefined), lead dev of FLO project

Wait what? That’s it? No smart contract, no mess of OP_RETURN from bitcoin, no need to download the daemons? 

No. All I needed to learn was how to make a transaction.

### My first transaction in cryptocurrency

Ok… so I made another address (by the click of a button in the Alexandria wallet), and now I just needed to make a transaction, and BAM. 

I am not sure which one was my very first transaction of all, but this is my first transaction with comment: [b80cd](https://florincoin.info/tx/b80cdfabb5d42e7358e0e6ad01878aabebd0bba12c2c25d35691580ac6ec6851)…

### My first transaction programmatically 

It was more or less at this time that I discovered the Alexandria API and noticed what they call **“Client Library”**. Browsing the examples I found very interesting that I could send a transaction using **“FloVault”** (I had no idea what that was, but hey… there is so much to learn at once, gotta take it slow). 

Look how simple they made it look! If you want to make a transaction, you just have to sign in to your wallet:

![](https://cdn-images-1.medium.com/max/2000/1*pE9sPgRSP3c6lsnE2Pn4Pw.png)

and…

![](https://cdn-images-1.medium.com/max/2000/1*-XatVSkLkBAprQPQqyEhWQ.png)

BAM! Transaction magic will happen!!!

Ohhhh cool! Now I can write a few lines of javascript real quick to do that. I already have a wallet from Alexandria and… wait… this is a “client library” and I don’t want to expose the credentials of my wallet in the code (the your_identifier and your_password part of the declaration of the wallet).

Fine, I am sure I can write a Node command line application (server-side) that can do that in a heart beat. But it wasn’t so easy… 

I was so amazed by the simplicity of making a transaction programmatically that I failed to read the **highlighted** note in the Alexandria API documentation, that says:

![](https://cdn-images-1.medium.com/max/2000/1*VUZr-SF9yNrdd5cLlX-r2A.png)

and because I did not read it I got back in the Alexandria chat and ask: “Where can I find the SimpleWallet.js file?” They told me to download the new one, SimpleWlletFlorincoin.js, which I did, copied the file to my computer and tried to simply login to my wallet…

I don’t remember now if I succeeded to do that or not, but **I know for sure** that I could **not** make a transaction. Errors after errors and I thought I only needed to load the dependencies using *require* from node.js and done, but…
> What happened next was a battle trying to halfway understand what was called what and finding out the dependencies needed, but after a few hours I had a working combo of code that worked on server side… and they said it couldn’t be done.

You don’t need to hassle that yourself, just copy: [SimpleDeps.j](https://github.com/daviortega/flotorizer/blob/master/src/SimpleDeps.js)s and [SimpleWalletFlorincoin.js](https://github.com/daviortega/flotorizer/blob/master/src/SimpleWalletFlorincoin.js) from the [Flotorizer github](https://github.com/daviortega/flotorizer) and you are good to go. 
> This was a hack, the FLO team is working to release a npm package that will be able to do all that with even less hassle.

Now I finally could execute [my first transaction programmatically](https://florincoin.info/tx/aef827374442dd1688853a47051d90362d8a5d9b077013311823bb5570f0db59). Here is the code (or something like that):

<iframe src="https://medium.com/media/168f02d140553ba035db236db2a68f22" frameborder=0></iframe>

then I just had to run: node firstTransaction.js and right there I have written on the FLO Blockchain. Amazing, isn’t it?

## The birth of Flotorizer

Months earlier, in my collaboration with the California Pirate Party, I was thinking a lot about digital signatures, encryption and whatnot but all related to pursuit the development of a [voting system for liquid democracy](https://medium.com/@ortega_science/a-real-lab-for-liquid-democracy-b0ce54a40bb1). During that time I was interested in sha algorithms and how cool was that idea.

Well… it occurred to me that I could put the sha-512 signature of a file in the FLO blockchain. At that moment, I realized that I could prove that a file with a specific content **existed** at least at the time of the transaction.

Before I even thought about the rest, I already had a name for the application: Florincoin + notary + zer = Flotorizer. I even made a transaction for it: [f9a1…](https://florincoin.info/tx/f9a1ce8f34d03261817b905c0d08034bc25b9fbb827c7ae58de4f724920138f5)
> I know that the most accurate would be Flotarizer, but that doesn’t sound good at all… I thought about Flotary but that was too close to [Rotary](https://www.rotary.org/) so I decided to go with Flotorizer.

In my first transaction, I used the shasum command line unix application to calculate the digital signature of a file and the snippet above to insert it in the block chain: [8004…](https://florincoin.info/tx/8004104227dc5f59c6e817dbcd4d192d21c31118b1e2225133d0d0022b9c61b6)

That was the moment I realized (it was a week full of epiphanies), I not only could prove the existence of the file but… wait for it… 

**I didn’t even need to tell anyone what the file was about, at all**!!!

See, theSHA2 family of hash function generates a [unique *enough](https://en.wikipedia.org/wiki/Collision_resistance)* string for a given input. But you cannot figure out the input just by looking at the string. Thus, I can prove that a picture existed without showing it to anyone, only by calculating the sha-512 digital signature of the picture and posting on the FLO Blockchain.

If any one contested that the picture actually existed, then all I had to do is to calculated the signature with [any independent sha-512 calculator](https://md5file.com/calculator) and compare the result with the record in the Blockchain. No one can delete the record and the record is public, but nobody knows what it is proving until it is contested. Cool, huh?

Lastly, I realized that other people might want to use this too. So I thought about making the app public. The cost of a Flotorization is 0.001 FLOs in fees of the transaction and with 1 FLO at less than $0.10 I thought I could fund it with less than $1.00 and make the app free… and so I did.

So I decide to pack all that into a public app. But as a sympathizer of the pirates ideals of privacy, I wanted to have an app that was Zero Knowledge. I did not want to have any knowledge of what was flotorized

## The backbones of Flotorizer

This part is a bit more technical, but I promise that it is not that complicated.

I used the [crypto](https://nodejs.org/api/crypto.html) library of [Node.js](https://nodejs.org/en/) with [Webpack](https://webpack.js.org/) to build a code client-side that calculates the sha-512 digital signature of the file chosen by the user without having to **EVER** submit the file to the server.

That way, even as the creator of Flotorizer, I would never know what the file was about, even if I tried.

On the server-side, I used [express.js](https://expressjs.com/) to build literally two routes:

* /stats : Which returns the number of flotorizations so far

* /flotorize: a GET route that does all the magic

The client-side of the code, as soon as it finishes to calculate the digital signature, makes a GET request to/flotorize sending as parameters the sha-512 signature and the name of the file.

The server-side now attempts to make a transaction from my two addresses and puts the digital signature in the tx_comment field of the transaction:

    This document has been flotorized: 1ED58159ADCF54A4753083F706089A4BC0CEAA55A8E973D431E7E056CE034FD1D5925096689E5494608DF0F246AC24D7BC89ADDB039CBCC13B8FCC47C8C245AE
> By the way, I had to implement a lousy check to avoid double (or multiple) flotorizations of the same file. All because this hash 1ED5... has been flotorized probably over 100 times, haha. If the owner of the file is reading this, please let me know what the file that generates this signature is… or better yet, don’t :)

If the transaction is successful, the server-side code uses pdfkit to generate a PDF receipt with the information about the name of the file and the transaction. It also encodes the link for the transaction in the [FLO block explorer](https://florincoin.info) on a QR-code using qr-image.

As soon as the pdf is completed, server sends the pdf file back to the user and immediately deletes it from the server’s storage. No database is required, no long term storage, nothing, as simple as it gets.

With the code running locally, all I had to to is to pass it to [Heroku](http://heroku.com). To hide my credentials I use the Heroku environmental variables. Locally, I stripped the credentials from the code and use nf package to generate the environmental variables from a .env file that I sure included in my .gitignore.

And there you have it. A VERY simple code that can let you prove that a certain content in a file existed at least prior to the time of transaction.

Let me know if you have any questions or comments. I hope you too feel encouraged to adventure yourself in using this amazing infrastructure around the FLO Blockchain.

As for the future of Flotorizer, we are developing a new, more robust, version of it. We will always offer the current service for free and in the near future we will build a paid version (paid with FLOs only) that will offer the option to save your files as well. In that version, all the information will be encrypted client-side before it is sent to our servers, keeping the full privacy for our users.

 If you want to support this development, donate to:

* FLO: F8YfuREuqCtW8MNj5LADczLoskgSDaNskn

* LTC: LarUzkftuCjWi1sAL8An7o6wohdz4vJxTq

* BTC: 1ArSXxcNTPbofJ1p79cg3ATd3cB5reqXGB

* XMR: 4LBX9sXW8dR8Aa55wvZhRj6WAUD1Tej6caLVv2tdkPH54njhYKTKfVMNxAtzD4P5DmiM5FAAi7Esg7EkEU3u2a98FzRy82YMaqn1xDdZCw

If you want to donate in any other crypto currency, just let me know.
