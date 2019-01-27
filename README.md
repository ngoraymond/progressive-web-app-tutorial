## Introduction

In this tutorial, I’ll show you how to add your HTML, Javascript, and styling to this template to create an app that works online, offline, in a browser, and as a mobile app.

Progressive web apps (or PWAs) are a hybrid of a website and an app that you might use on a tablet or mobile. Making one has a lot in common with creating a website, but with a few key extra files and concepts involved.

This post will show you how to make one that you can then host, use online as a website, and use offline and as a mobile app.

To give an example of what you could create, here is an example of a web app. It generates a QR code from the text you enter.

[qr-code-pwa.firebaseapp.com](https://qr-code-pwa.firebaseapp.com/)

## The Basics

In most ways, progressive web apps are created in the same way as a typical website. The foundation and text are built using HTML, styling is done with CSS, and functionality is added with JavaScript. In this tutorial, the principal components discussed below have already been added to the provided template, but they are important to understand.

### Caching

For progressive web apps, it is important that files are cached to enable offline functionality. "Cached" means that the shell files are loaded once over the network and then saved to the local device. Every subsequent time that the user opens the app, the shell files are loaded from the local device's cache, which results in faster startup times and enables offline mode.

Progressive web apps use service workers to cache files. A service worker is a script that your browser runs in the background, separate from a web page, opening the door to features that don't need a web page or user interaction. For this tutorial, our service worker will NOT cache files because this allows us to make changes to our app without needing to constantly clear the cache.

### App Manifest

App manifests are declared with a manifest.json file. The web app manifest is a simple JSON file that gives you, the developer, the ability to control how your app appears to the user in the areas that they would expect to see apps (for example the mobile home screen), direct what the user can launch and more importantly how they can launch it.

### Overview of the repository

The main files are:

- [public/index.html](public/index.html) The main page for your app
- [public/style/style.css)](public/style/style.css) Add your own styling to this file
- [public/scripts/app.js](public/scripts/app.js) This contains the javascript to handle the logic in your app. It currently uses localStorage for storing data when the use clicks the button, it is recommended to use another database in production, such as indexedDb (Read more [here](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/#intercept_the_network_request_and_cache_the_response))
- [images/icons](images/icons) Create square icons of the number of pixels for each size and save them here
- [public/service-worker.js](public/service-worker.js) Update this with the list of files you want to cache locally

### Default appearance of the app

<img src="images/template-progressive-web-app.png" width="400" border="3" style="border-radius: 10px;">

## Create your app

First, clone this repository. Then open it in a code editor.

### Required lines for iOS and Windows

In order for the app to function properly on IOS and Windows, a few lines will need to be added index.html. Copy and paste the follwing code snippet into where it says ``` <!-- Add to home screen for Safari on iOS --> ``` and ```<!-- Tile Icon for Windows -->``` in the file index.html.

```
  <!-- Add to home screen for Safari on iOS -->
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black">
  <meta name="apple-mobile-web-app-title" content="Weather PWA">
  <link rel="apple-touch-icon" href="images/icons/icon-152x152.png">
  <!-- Tile Icon for Windows -->
  <meta name="msapplication-TileImage" content="images/icons/icon-144x144.png">
  <meta name="msapplication-TileColor" content="#2F3BA2">
```

### Personalize your app

Then, navigate to index.html and find ```<span class="card-title">Your message</span>```.
Replace "Your message" with "[Your name]'s message." 
Ex: ```<span class="card-title">Richard's message</span>```

Now, you're ready to deploy your app!

## Test out the sample app by deploying to Firebase

If you're new to Firebase, you'll need to create your account and install some tools first.

- Create a Firebase account at https://firebase.google.com/console/. Note: Use your personal email because school emails will not work!
- If you do not already have Node.js and npm installed, install them from https://www.npmjs.com/get-npm
- Install the Firebase tools via npm by typing the following into the command line: npm install -g firebase-tools

Once your account has been created and you've signed in, you're ready to deploy!
- Create a new app at https://firebase.google.com/console/
- Update your credentials: firebase login
- Add your project by typing "firebase use --add" and select your project from the list. Proceed with the instructions shown.
- Finally, deploy the app to Firebase: firebase deploy
- Celebrate. You're done! Your app will be deployed to the domain: https://YOUR-FIREBASE-APP.firebaseapp.com

[More instructions for deploying to firebase](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/#deploy_to_firebase)

## Launch the app on your mobile device

### IOS

- Navigate to your app's domain using Safari
- Tap the Share button at the bottom
- Tap the icon labeled Add to Home Screen.
- Name the app and tap Add in the upper-right corner
- Your app should now be on your home screen

### Android

- Navigate to your app's domain using Chrome or any other browser: 
- After some time, a notification should pop up with a "+Add to Home Screen" message
- Click it and your app should now be on your home screen

## Afterwards

Try playing around and personalizing the app a little bit. Then, deploy the project again to try it out! If anything fails to update, try clearing the browser data through settings.

When you feel you are ready to enable caching, navigate to public/service-worker.js and uncomment the block of code within the variable filesToCache. Once you enable caching, you will need to delete the browser cache within settings every time you make changes to your app.

Feel free to use this repo as your template for any future creations!

Note that many of the concepts used for PWAs (HTML, CSS, JS) are the same as those used for developing webpages. I recommend learning from other tutorials on web development if you are not familiar with these concepts.

If you wish to learn more about the unique capabilities of PWAs, I recommend the following tutorial: [Your First Progressive Web App - Google Developers](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/)

## What's included

The following files can and should be modified:

- [public/index.html](public/index.html) The main page for your app
- [public/style/style.css)](public/style/style.css) Add your own styling to this file
- [public/scripts/app.js](public/scripts/app.js) This contains the javascript to handle the logic in your app. It currently uses localStorage for storing data when the use clicks the button, it is recommended to use another database in production, such as indexedDb (Read more [here](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/#intercept_the_network_request_and_cache_the_response))
- [images/icons](images/icons) Create square icons of the number of pixels for each size and save them here
- [public/service-worker.js](public/service-worker.js) Update this with the list of files you want to cache locally

```
├── README.md
├── firebase.json
└── public
    ├── fonts
    │   └── roboto
    │       └── ...
    ├── images
    │   └── icons
    │       └── ...
    ├── index.html
    ├── manifest.json
    ├── scripts
    │   ├── app.js
    │   ├── jquery-3.3.1.js
    │   └── materialize.js
    ├── service-worker.js
    └── styles
        ├── materialize.css
        └── style.css
```

- [JQuery](https://jquery.com/) A library for supporting quick and easy javascipt in your website
- For styling, this has materialize.js and css from [materializecss.com](http://materializecss.com/). Remove or replace it if you prefer something different.
- [public/service-worker.js](public/service-worker.js) Currently this will cache the app's files for quick local access. Read more about Service Workers [here](https://developers.google.com/web/fundamentals/primers/service-workers/).
- [public/manifest.json](public/manifest.json) A JSON file specifies how your app appears to the user in the areas that they would expect to see apps (for example the mobile home screen), direct what the user can launch and more importantly how they can launch it. Read more about this [here](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/#support_native_integration).


## Examples

Here is an example hosted on firebase:
- [ryanwhocodes/qr-code-pwa](https://github.com/ryanwhocodes/qr-code-pwa)
- [qr-code-pwa.firebaseapp.com/](https://qr-code-pwa.firebaseapp.com/)

## Resources

- Tutorial on Medium - [How you can make a progressive web app in an hour – freeCodeCamp](https://medium.freecodecamp.org/how-you-can-make-a-progressive-web-app-in-an-hour-7e36d560610e)
- [Your First Progressive Web App - Google Developers](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/)
