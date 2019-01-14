## Introduction

In this tutorial, I’ll show you how to add your HTML, Javascript, and styling to this template to create an app that works online, offline, in a browser, and as a mobile app

Progressive web apps are a hybrid of a website and an app that you might use on a tablet or mobile. Making one has a lot in common with creating a website, but with a few key extra files and concepts involved. It need not take a week of trial and error or trawling through a tutorial to get one up and running.

This post will show you how to make one in an hour that you can then host, use online as a website, and use offline and as a mobile app.

To give an example of what you could create, here is an example of a web app. It generates a QR code from the text you enter.

[qr-code-pwa.firebaseapp.com](https://qr-code-pwa.firebaseapp.com/)

## The Basics

In most ways, progressive web apps are created in the same way as a typical website. The foundation and text are built using HTML, styling is done with CSS, and functionality is added with JavaScript.

The app's shell is the minimal HTML, CSS, and JavaScript that is required to power the user interface of a progressive web app and is one of the components that ensures reliably good performance. Its first load should be extremely quick and immediately cached. "Cached" means that the shell files are loaded once over the network and then saved to the local device. Every subsequent time that the user opens the app, the shell files are loaded from the local device's cache, which results in blazing-fast startup times.

App shell architecture separates the core application infrastructure and UI from the data. All of the UI and infrastructure is cached locally using a service worker so that on subsequent loads, the Progressive Web App only needs to retrieve the necessary data, instead of having to load everything.

A service worker is a script that your browser runs in the background, separate from a web page, opening the door to features that don't need a web page or user interaction.


Declare an app manifest with a manifest.json file

The web app manifest is a simple JSON file that gives you, the developer, the ability to control how your app appears to the user in the areas that they would expect to see apps (for example the mobile home screen), direct what the user can launch and more importantly how they can launch it.

Add to Homescreen elements for Safari on iOS
In your index.html, add the following to the bottom of the ```<head>``` element:

```
  <!-- Add to home screen for Safari on iOS -->
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black">
  <meta name="apple-mobile-web-app-title" content="Weather PWA">
  <link rel="apple-touch-icon" href="images/icons/icon-152x152.png">
```

Tile Icon for Windows
In your index.html, add the following to the bottom of the ``<head>`` element:

```
  <meta name="msapplication-TileImage" content="images/icons/icon-144x144.png">
  <meta name="msapplication-TileColor" content="#2F3BA2">
```

## Create your app

Clone this repo (or just copy the bits you need). The main files to edit are:  

- [public/index.html](public/index.html) The main page for your app
- [public/style/style.css)](public/style/style.css) Add your own styling to this file
- [public/scripts/app.js](public/scripts/app.js) This contains the javascript to handle the logic in your app. It currently uses localStorage for storing data when the use clicks the button, it is recommended to use another database in production, such as indexedDb (Read more [here](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/#intercept_the_network_request_and_cache_the_response))
- [images/icons](images/icons) Create square icons of the number of pixels for each size and save them here
- [public/service-worker.js](public/service-worker.js) Update this with the list of files you want to cache locally

<img src="images/template-progressive-web-app.png" width="400" border="3" style="border-radius: 10px;">
















## Using the app

- Open `index.html` within the public folder
- Install a service worker for your browser, if you haven't already (eg [Web Server for Chrome](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/#install_and_verify_web_server))
- Browsers may also ask if you want to include the app on your homescreen

## What's included

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

## Hosting

- Sign up to firebase  
- Download and install the firebase CLI tools  
- Within your project folder:
  - `firebase init`
  - `firebase deploy`

[More instructions for deploying to firebase](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/#deploy_to_firebase)

## Examples

Here is an example hosted on firebase:
- [ryanwhocodes/qr-code-pwa](https://github.com/ryanwhocodes/qr-code-pwa)
- [qr-code-pwa.firebaseapp.com/](https://qr-code-pwa.firebaseapp.com/)

## Resources

- Tutorial on Medium - [How you can make a progressive web app in an hour – freeCodeCamp](https://medium.freecodecamp.org/how-you-can-make-a-progressive-web-app-in-an-hour-7e36d560610e)
- [Your First Progressive Web App - Google Developers](https://developers.google.com/web/fundamentals/codelabs/your-first-pwapp/)
