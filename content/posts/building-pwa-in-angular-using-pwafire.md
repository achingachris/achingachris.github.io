---
author: ["Chris Achinga"]
title: "Building Progressive Web Apps in Angular (using pwafire)"
date: "2023-12-12"
description: "Progressive Web Apps(PWA) are basically sites that use modern web tools to provide app-like experiences to users."
tags: ["angular", "progressive web apps", "pwafire"]
ShowToc: true
---



Progressive Web Apps(PWA) are basically sites that use modern web tools to provide app-like experiences to users.

https://web.dev/explore/progressive-web-apps

Progressive Web Apps (PWA) are built and enhanced with modern APIs to deliver enhanced capabilities, reliability, and installability while reaching *anyone, anywhere, on any device* with a single codebase: https://web.dev/articles/what-are-pwas

PWAs is a very interesting topic when it comes to user experiences and why businesses would use it. It comes down to users needs and organization goals and agenda, but hear me out:

* **PWAs are faster than traditional websites.** This is because they are able to cache content locally, which means that they can load much faster, even on slow internet connections.
    
* **PWAs are more reliable than traditional websites.** This is because they are not reliant on the internet in order to function. Once a PWA has been installed, it can be used offline.
    
* **PWAs are more engaging than traditional websites.** This is because they can offer a number of features that are not available on traditional websites, such as push notifications and home screen icons.
    
* **PWAs can be installed on users' home screens.** This makes them more likely to be used, as they are always just a tap away.
    
* **PWAs can lead to increased conversion rates.** This is because they offer a more seamless and engaging user experience.
    
* **PWAs can lead to more repeat visitors.** This is because they are more likely to be used than traditional websites.
    
* **PWAs can lead to higher revenue.** This is because they can lead to increased conversion rates and more repeat visitors.
    

Overall, there are a number of reasons why businesses are using PWAs. They offer a number of benefits over traditional websites, and they can help businesses to achieve their goals.

# How Does Angular Support PWA?

![](/images/past/angular-pwa.png)

Simply, service workers.

https://angular.dev/ecosystem/service-workers/

At its simplest, a service worker is a script that runs in the web browser and manages caching for an application.

A service worker acts as a proxy between web applications, browser, and the network(if available). They enhance applications to deliver a reliable user experience and performance. Adding a service worker on an Angular app is the first step to creating a PWA(in Angular).

Service Workers helps single-page applications built with Angular get the best performance and makes the applications highly reliable. All this is done without the need to code against low-level APIs.

### So… How do you have these service workers in your Angular app?

Pretty simple, actually. You just need to run this command:

```plaintext
ng add @angular/pwa
```

Okay, this command does a couple of things to make that Angular app you have a PWA, here’s a breakdown:

1. Adds the `@angular/service-worker` package to your project, which in turn creates a service worker, and supports service worker builds in the CLI.
    
2. Updates the `index.html` file:
    
    * Includes a link to add the `manifest.webmanifest` file
        
    * Adds a meta tag for `theme-color`
        
3. Creates the service worker configuration file called `ngsw-config.json`, which specifies the caching behaviors and other settings.
   https://angular.dev/ecosystem/service-workers/config

To make it happen, you may need to build you app (again 🤣)

```plaintext
ng build
```

PS: You can actually get in depth content on the service workers on the Angular Docs, it’s are surprisingly well documented tbh 🤓

https://angular.dev/ecosystem/service-workers/getting-started

What happens when you run your app? The fastest way to identify a PWA is by checking the install icon on a Chrome address bar, just like the image below;

![](/images/past/install-pwa.png)

## PWAFIRE … (wth is that)

![](/images/past/pwafire.png)

It’s not related to fire, or any of the 4 elements of the earth, It’s just collection of resources/APIs used to build Progressive Web Apps.

https://pwafire.org/

PWA brings a lot to the table, with 22 APIs for developers to explore! My best APIs from pwafire:

1. Connectivity
    
2. Copy Image
    
3. Copy Text
    
4. Notifications
    
5. Custom install
    
6. Share
    
7. Display mode
    
8. Fullscreen
    
9. Idle detection
    

You can check others out (my opinions can be sad).

https://docs.pwafire.org/get-started

## Code and Demo

![chris achinga](/images/past/codedemo.png)

This is a funny one, a simple Angular app that is a PWA using some pwafire APIs to make it cool.

In case you’re more of a not-long read, here’s the source:

https://github.com/achingachris/dad-jokes

Using the Share and Copy Text API to make a Progressive Web App.

From the source code on the repo shared, we will focus on the [app.component.ts](https://github.com/achingachris/dad-jokes/blob/main/src/app/app.component.ts) file:

Remeber to install pwafire in your application by running the command:

```plaintext
npm i pwafire --save
```

### Using Copy Text API:

This API is used for reading and writing text data to the clipboard, without blocking the main thread.

https://docs.pwafire.org/copy-text

The copy text API usage is as follows:

```typescript
const text = "Text to copy"
pwa.copyText(text);
```

So, inside our application, we will get the tex from the API response:

```typescript
  async copyJoke(joke: string) {
    try {
      const res = await pwa.copyText(joke);
      this.jokeCopied = res.ok;
      setTimeout(() => (this.jokeCopied = false), 5000);
    } catch (error) {
      console.log(error);
    }
  }
```

### Using Share API:

Share links, text, and files to other apps installed on the device.

https://docs.pwafire.org/web-share

To use the share API, you first define the content to be shared:

```typescript
const data = 
{ 
    title: "Some title..", 
    text: "Some text...", 
    url: "https://pwafire.org", 
};
```

And finally share the data:

```typescript
pwa.Share(data);
```

So, here is how it’s used inside our app:

```typescript
  async shareJoke() {
    const shareOptions = {
      title: 'Check out this joke!',
      text: `${this.joke} @WTM_Pwani #DevFestPwani #DevFest2023 #askmoringa @moringaschool @OnlyDevs_Ke`,
      url: 'https://dadjokes-phi.vercel.app/',
    };
    

    try {
      await pwa.Share(shareOptions);
    } catch (error) {
      console.log(error);
    }
  }
```

Simple right!

![demo](/images/past/installpwa.png)

You can checkout the live demo here:

https://dadjokes-pwa.vercel.app/

That’s it good people. By the way, there’s a lot to learn in the PWA topic, I will drop some links below, just in case you are interested. Especially if you are curious on whether you can add a Progressive Web App to playstore 😎

Pwafire documentation: https://docs.pwafire.org/

Adding a PWA on Google Playstore: https://developers.google.com/codelabs/pwa-in-play#0

Fugu API tracker: https://fugu-tracker.web.app/

Fugu APIs: https://developers.google.com/learn/pathways/fugu-apis

Angular Service Workers: https://angular.dev/ecosystem/service-workers

Explore PWA: https://web.dev/explore/progressive-web-apps
