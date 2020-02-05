---
title: "Behind Pokedex5E - Part 1"
published: true
---

Mid January 2019 I saw a post on reddit titled _"Pokemon in 5th Edition - Generation III Update!"_. As I grew in the 90s, playing Pokémon games and watching the animé, I was looking forward to trying out this homebrew system with a couple of friends!

After a few weeks I managed to convince two close friends to play a one-shot with me. As we played I started to realize that there was a _lot_ of book-keeping involved in running this homebrew. If you have ever played Dungeon and Dragons, imagine that for every Pokémon you catch, the player will have to write up a "mini character". My first thought after playing this session was: _How can I speed up catching and collecting Pokémon?_. The answer was obvious, the player could use the one thing most people will never leave at home - their phone!

</br>
</br>

### First Prototype
<div class="container">
<div class="img-inline">
    <figure >
        <img src="/img/pokemon5e/initial_prototype.png" class="img-figure">
    </figure>
</div>
First of all, I had to see if I could get the data for all moves, Pokémon and whatever else would be needed. Luckily the <a href="https://twitter.com/joethedm">creator</a> of the system is a bit of a google sheet wizard and provided a couple of sheets that players could use to keep track of their Pokémon. In these sheets were also all data, for all Pokémon! I started to throw together a super quick prototype the next day. 


I signed up as a developer to get access to the google API, and created a service account that I shared the google sheets with. I then used Python and the module [gspread](https://github.com/burnash/gspread) to simply download the google sheets as csv. I then used a few different scripts to convert the csv data-structure to json-format. Unfortunately it is not a simple 1-to-1-conversion. As there was a lot of information that I needed to parse out of blocks of text. I did this with a bunch of regexp.

As time passed and more generations were released the harder it got to parse the texts for needed information. This means that I always have to check the differences and check that nothing sneaks in that shouldn't be there. An area for improvements in the future.

As you can see above, the prototype was incredibly simple and ugly, but as previously stated, I was mainly testing if I could get the data.
</div>

</br>
</br>

### A.. style?
<div class="container">
<div class="img-inline">
    <figure >
        <video autoplay="autoplay" loop="loop" width="768" height="512" class="img-figure">
          <source src="/img/pokemon5e/first_release.webm" type="video/webm">
        </video>
        <figcaption> <i>Right click and play</i> </figcaption>
    </figure>
</div>

Having proven to myself that I could get the data, without manually copying it from the manual, I decided that I should actually make a stab at it, and 4 days later I had a fairly simple app that did stuff! It had all Pokémon that were released at the time (up to gen 3) and all the moves, abilities and such. You could keep an infinite (in theory at least, in practice your device memory would run out) amount of them and switch them between your party and your storage. I am the first to admit that I am not an artist, so it looked quite awful but it sure did the job. I made a debug android build and shared it with the Pokémon 5E discord community and people thought it was super cool!
</div>

</br>
</br>


### I am not alone!
<div class="container">
<div class="img-inline">
    <figure >
        <video autoplay="autoplay" loop="loop" width="768" height="512" class="img-figure">
          <source src="/img/pokemon5e/second_release.webm" type="video/webm">
        </video>
        <figcaption> <i>Right click and play</i> </figcaption>
    </figure>
</div>

The positive feedback spurred me to continue working on it. I got help from Roberta Tam for a UI refresh (you can read more about her foray into this project here <a href="https://www.birdietam.com/p5e.html">https://www.birdietam.com/p5e</a>. Over the coming few weeks I added tons of fixes and features: profiles and crash-tracking, as well as extended the editor screen to support Evolving Pokémon as well as Nicknames. But it wasn't long before Roberta wanted to change the style - again.
</div>

</br>
</br>

### The UI update
<div class="container">
<div class="img-inline">
    <figure >
        <video autoplay="autoplay" loop="loop" width="768" height="512" class="img-figure">
          <source src="/img/pokemon5e/third_release.webm" type="video/webm">
        </video>
        <figcaption> <i>Right click and play</i> </figcaption>
    </figure>
</div>
A month after the first UI update, Roberta came up with something else for the UI; while the first style was a throwback to D&D and Pokémon this one was simpler and made all information more readable.

Every update brought on issues that users found, as well as ideas, from both us as creators and from the community. Because of the nature of the app it was incredibly hard to find issues without comparing every Pokémon and Move between the app and the rule books. So naturally, as people played the game they saw things that didn't match and reported it. I alsocreated a bunch of Python scripts that "validated" the data. This caught issues that were easy to detect, such as formatting errors in the source, that lead to errors in the parsed data down the line.

At this point, the app had been "out" for a month. Saying it had been "out" may be a stretch, as it was Android-only, and distributed through a Google Drive. After the new, fancier GUI design, I was eager to publish it onto Google Play. Putting it onto Google Play was incredibly easy (really made me understand why there are so many "trash apps" on that platform), and only took a few hours of figuring stuff out and then a few more waiting for it to be published.

</div>

</br>
</br>

### iOS when?
<div class="container"> 
One of the most asked questions in regards to the app was, maybe to no one's surprise: "Will there be an iOS version?" I always had plans to release a version for iOS as well, but the barrier of entry into the iOS market is significantly higher. For me, the biggest problem was that you need to build your iOS app on a macOS machine. Therefore, the first issue was to get a machine to develop it on. I went online, and after a few days of looking around I found a mac mini for about $60. I signed up as an iOS dev, which is another $100 annually. With this little machine I decided to set up <a href="https://jenkins.io/">Jenkins</a> - you can read more about my foray into Jenkins in a future post (if I get around to it).

The app was first uploaded onto Apple store 13th of May, which was 8 days after it was uploaded to Google Play. However, the app was not accepted until the 28th of May.

Setting up Jenkins made it a lot easier to create builds, as it was only a few clicks in a web interface. Because of the reduced obstacles in building and installing, I ended up testing a lot more, which decreased the amount of bugs that were shipped in each version. This shows that easier workflows make for better products!

</div>

</br>
</br>

### The end
<div class="container">
The story doesn't end here! There is still more to tell so stay tuned for a part 2. 
</div>