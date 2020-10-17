# Firebase Exploration

An exploration journal for Firebase (a Google Developer Product) by **Amar Fadil** (NIM 16520008)

## Preface

Before I started this journal, I've been interested in learning about google's product. I did use their [**Google Cloud Platform**](https://cloud.google.com/), especially their Compute Engine, and it's just excellent, though a little bit *pricey* for me lmao (free trial credit is enough tho). After that, I heard about this product called [**Firebase**](https://firebase.google.com/). It was okay, but I don't know how does it works or how to create the app, just to getting started with it. So, I did a little research in just a day and here you go, the **Buku Tamu** [website](https://marfgold1.github.io/bukutamu/) (Hosted with ❤️ by Github) and [public repo](https://github.com/marfgold1/bukutamu).

## Behind the Buku Tamu: Section 1

On Oct 17th, 2020, exactly the day when I created this journal, I started by doing some research on Github Pages with Firebase and found [this article](https://medium.com/pan-labs/dynamic-web-apps-on-github-pages-for-free-ffac2b776d45). In creating the idea, I don't want to make it complicated, implementing the [KISS (Keep It Simple, Stupid)](https://youtu.be/HjZ6AfFHhSM?t=7628) principle that motivates me lol. So, I tried to ideate the web that I want to create: it's a guest book, where everyone can send messages anonymously, like an internet forum or message-board.  Of course, to KISS (because I only have one day to do it, or 6 hours to be exact), I made it more simple: no one can delete their message and only text message is supported. With that in mind, I begun building my site with (Bootstrap Studio)[https://bootstrapstudio.io/] and a little bit of custom javascript here and there.

## The Code: Section 2

To make the website more dynamic (and integrate to Firebase), I have to code a little bit. Oh yeah, Firebase has a looooooot of stuff in it, there are [Authorization](https://firebase.google.com/products/auth), [Cloud Firestore](https://firebase.google.com/products/firestore), [Realtime Database](https://firebase.google.com/products/realtime-database), [Storage](https://firebase.google.com/products/storage), and many more! And no, obviously, I'm not going to use all of them, duh! In this case, I use **Realtime Database** to do the work. The script that I used in **Buku Tamu** is relatively simple (or at least that I was thought):

1. Initialize a Firebase application instance and get a reference to the database service
  ```js
  // Set the configuration for your app
  // TODO: Replace with your project's config object
  var config = {
    apiKey: "apiKey",
    authDomain: "projectId.firebaseapp.com",
    databaseURL: "https://databaseName.firebaseio.com",
    storageBucket: "bucket.appspot.com"
  };
  firebase.initializeApp(config);

  // Get a reference to the database service
  var database = firebase.database();
  ```
2. Listen to ref event when a child is added or removed
  ```js
  var commentsRef = firebase.database().ref('ref_url');
  commentsRef.on('child_added', function(data) {
    // add message on the board
  });
  commentsRef.on('child_removed', function(data) {
    // delete specified message on the board
  });
  ```
3. Create a function to save a message to firebase
  ```js
  function saveToFirebase(message) {
    var msgObject = {
      msg: message
    };
    msgDbRef.push()
            .set(msgObject)
            .then(function(snapshot) {
              // success event
            }, function(error) {
              // error event
            });
  }
  ```
4. And that's basically it! (well, uh, the rest is up to the implementation details e.g. cloning DOM, setting message timeout, etc, I'm not going to spill it here)

There you go, I've finished my website, and here's how it looks:
![Main Page](https://github.com/marfgold1/firebase-exploration/raw/main/main_page.png)
It's as simple as that (uh actually there's more details but that's what I can tell you for now lol).

## Addendum
So, what are you waiting for? Check [the website out now!](https://marfgold1.github.io/bukutamu/) and the [repo](https://github.com/marfgold1/bukutamu) (the script is minified, if you are interested to learn the full code, feel free to contact me!). That's it basically, and oh you can try to built yourself a Firebase-integrated website with my tutorial in this journal! Anyway, thank you for reading the journal, it was fun when it lasted! See you in the next journal!

>Semarang, October 17th 2020
>
>Amar Fadil
