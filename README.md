# Create Progressive Web App for any React Application

## What is Progressive Web App

It adds website install options just similar to any desktop and mobile applications. It supports and can be installed on windows/linux/mac/android using chrome & Ios/Ipad using safari.

## Add PWA support to the React App

Skip to Add PWA dependencies section for an existing react application


## Getting Started with Create React App for new application


Create a new react app with [Create React App](https://github.com/facebook/create-react-app).

## Add PWA dependencies

If not available, add below packages in dependencies section of package.json in the root folder.

```
"@testing-library/jest-dom": "^5.13.0",
"@testing-library/react": "^11.2.7",
"@testing-library/user-event": "^12.8.3",
"react": "^17.0.2",
"react-dom": "^17.0.2",
"react-scripts": "4.0.3",
"web-vitals": "^1.1.2",
"react-router-dom": "^5.2.0",
"workbox-background-sync": "^5.1.4",
"workbox-broadcast-update": "^5.1.4",
"workbox-cacheable-response": "^5.1.4",
"workbox-core": "^5.1.4",
"workbox-expiration": "^5.1.4",
"workbox-google-analytics": "^5.1.4",
"workbox-navigation-preload": "^5.1.4",
"workbox-precaching": "^5.1.4",
"workbox-range-requests": "^5.1.4",
"workbox-routing": "^5.1.4",
"workbox-strategies": "^5.1.4",
"workbox-streams": "^5.1.4"
```

## Install npm dependencies

Run below command to install the dependencies

`npm i`

## Add Service worker to the app

Add [service-worker.js](src/service-worker.js) and [serviceWorkerRegistration.js](src/serviceWorkerRegistration.js) files to the project src folder.


Add [worker.js](public/worker.js) file to the project public folder.

## Register the service worker

Add below import in [public/index.js](public/index.js)

```
import * as serviceWorkerRegistration from './serviceWorkerRegistration';
```

Add below code to register the service worker in [public/index.js](public/index.js)

```
// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://cra.link/PWA
serviceWorkerRegistration.register();
```

Check for the unregister() function for any service worker available in [public/index.js](public/index.js) and comment it.

```
//serviceWorkerRegistration.unregister();
```

Add below code in [public/index.html](public/index.html) to register a worker.

```
<script type="text/javascript">
    if ('serviceWorker' in navigator) {
      window.addEventListener('load', function () {
        navigator.serviceWorker.register('%PUBLIC_URL%/worker.js').then(function (registration) {
          console.log('Worker registration successful', registration.scope);
        }, function (err) {
          console.log('Worker registration failed', err);
        }).catch(function (err) {
          console.log(err);
        });
      });
    } else {
      console.log('Service Worker is not supported by browser.');
    }
</script>
```

## Configure icons for your app

Add icons of dimensions: 192x192 & 512x512 of your app to the public folder. Reference [public/logo192.png](public/logo192.png) and [public/logo512.png](public/logo512.png)

Add below in icons sections to configure icons in [public/mainfest.json](public/mainfest.json). You can also configure app name, favicon etc for your app.

```
{
    "src": "logo192.png",
    "type": "image/png",
    "sizes": "192x192"
},
{
    "src": "logo512.png",
    "type": "image/png",
    "sizes": "512x512"
}
```

Add Apple touch icon code in your head section of [public/index.html](public/index.html)

```
<link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
```

## Troubleshoot if your app is installable or not

Go to Chrome Dev Tools : Lighthouse

Select Progressive web app & generate report

Check report to see missing configurations for the support of installable pwa

## Available Scripts

In the project directory, you can run:

### Run `npm start` to test the app

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### Run `npm run build` to deploy the app

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.


### Reference

[Making a Progressive Web App](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

[Check PWA Supported browsers](https://caniuse.com/?search=pwa)

[Convert existing react app to PWA](https://medium.com/@toricpope/transform-a-react-app-into-a-progressive-web-app-pwa-dea336bd96e6)
