---
title: "Behind Pokedex5E"
published: true
---

Mid January 2019 I saw post on reddit about titled _"Pokemon in 5th Edition - Generation III Update!"_ having grown up in the 90s playing Pokémon games and watching the anime I was intrigued to try out this homebrew system with a couple of friends!

After a few weeks I managed to convince two close friends to play a one-shot with me. As we played I started to realise that there was a _lot_ of book keeping involved in running this homebrew, if you have ever played Dungeon and Dragons imagine that for every Pokémon you catch the player will have to write up a "mini character". My first though after playing this session was _How can I speed up catching and collecting Pokémon?_. The answer is of course very obvious, the player should could use the one thing most people will never leave at home - their phone! 

### First Prototype
<div class="container">
<img src="/img/pokemon5e/initial_prototype.png" class="img-inline">
First of I had to see if I could get the data for all moves, pokemons and what ever else would be needed. Luckily the [creator](https://twitter.com/joethedm) of the system is a bit of a google sheet wizard and also provided a couple of sheets that players could use to keep track of their Pokémon, in these sheets there was also all data for all Pokémon! I started to throw together a super quick prototype the next day. 


I signed up as a developer to get access to the google API and created a service account that I shared the google sheets with. I then using python and the module [gspread](https://github.com/burnash/gspread) to simply download the google sheets as csv. I then use few different script to convert it to json. Unfortunatelly it isn't a simple 1 to 1 conversion as there is a lot of information that I need to parse out of blocks of text, I do this with a bunch of regexp.

As time have moved on and more generations have been released the harder it have become to parse for the texts for need information, that means that I always have to check the diff and check so nothing sneaks in that shouldn't be there. An area for improvements in the future.

The prototype was incredibily simple and ugly (as you can see above) but as I mentioned I was mainly testing if I could get the data.
</div>

### A.. style?

<div class="container">
<video autoplay="autoplay" loop="loop" width="768" height="512" class="img-inline">
  <source src="/img/pokemon5e/first_release.webm" type="video/webm">
</video>
Having proven to myself that I could get the data without manually copying it down from the manual I decided that I should actually make a stab at it and 4 days later I had a fairly simple app that did stuff! It had all Pokémons that were released at the time (up to gen 3) and all the moves, abilities and such. You could keep an infinite (in theory at least, in pratice your device memory would run out) amount of them and switch them between your party and your storage. I am  the first to admit that I am not an artist (I guess one could argue that I _technically_ am one) so it looked quite awful but it sure did the job, I made a debug android build and shared it with the Pokemon 5E discord community and people thought it was super cool! 
</div>


### I am not alone!

<div class="container">
<video autoplay="autoplay" loop="loop" width="768" height="512" class="img-inline">
  <source src="/img/pokemon5e/second_release.webm" type="video/webm">
</video>
The positive feedback spured me to continue working on it, I got help from <a href="https://www.birdietam.com/">Roberta Tam</a> for a UI refresh (you can read more about her foray into this project here <a href="https://www.birdietam.com/p5e.html">https://www.birdietam.com/p5e</a>. Over the comming few weeks I added tons of fixes and features. Profiles, Crash Tracking and exteded the editor screen to support Evolving Pokémon as well as Nicknames. But it wasn't long before Roberta wanted to change the style - again.
</div>


### The UI update
<div class="container">
<video autoplay="autoplay" loop="loop" width="768" height="512" class="img-inline">
  <source src="/img/pokemon5e/third_release.webm" type="video/webm">
</video>

A month after the first UI upgrade Roberta came up with something else for the UI, while the first style was a throwback to D&D and Pokemon this one was simpler to help all information be easier to read.

Every update brought on issues that users found as well as ideas, both from us as creators and from the community. Because of the nature of the app it was increadibly hard to find issues without comparing every Pokémon and Move between the app and the rule books. So naturally as people played the game they saw things that didn't match and reported it. I also created a bunch of python scripts that "validated" the data, this caught issues that where easy to detect such as formatting errors in the source that lead to errors in the parsed data down the line.

At this point the app had been "out" for a month. Saying it had been "out" is maybe a stretch as it was only Android only and distributed through a Google Drive. Now after the new fancy gui style I was eager to publish it onto Google Play. Putting it onto Google Play was increadibly easy (really made me understand why there are so many "trash apps" on that platform) and only took a few hours of figuring stuff out and then a few of waiting for it to be published.
</div>

### iOS when?
<div class="container">
One of the most asked questions in regards to the app where, maybe unsurprisigly, "Will there be an iOS version?". I always had plans to release a version for iOS too, but the bar of entry into the iOS market is significally higher. For me the biggest problem was that you need to build your iOS app on a macOS machine. Therefore the first issue was to getting something to build it on, so I went online and after a few days looking I round I found a mac mini for about 60$ I then signed up as a iOS dev which is another 100$ annually. With this little machine I decided to setup <a href="https://jenkins.io/">Jenkins</a> on it too - you can read more about my foray into Jenkins in a different post. 



</div>

# Timeline
Mid January 2019 - Saw the redit post

End of January - Played the first time

January 31  - Started the Prototype

Febrary 1   - Ended the Prototype
Febrary 1   - Started Pokedex5e
Febrary 4   - 0.1.0, First "public" release through discord
Febrary 8   - Roberta joins
Febrary 11  - First UI style goes in
Febrary 12  - first
Febrary 13  - 0.3.0 First Reddit Post about the app

Mars 10     - Roberta starts on new ui design
Mars 21     - I start implementing the new UI
Mars 27     - New UI fully implemented

May 5       - 0.9.8 First upload and release on Google Play
May 13      - 0.9.17 First Upload to iOS
May 28      - 0.9.17 Upload is accepted on iOS 

April 12    - Game Analytics
June 21     - Survey