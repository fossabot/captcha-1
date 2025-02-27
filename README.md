# JSE Captcha
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2FAremixdj%2Fcaptcha.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2FAremixdj%2Fcaptcha?ref=badge_shield)


**[JSECOIN](https://jsecoin.com/)** [THE FUTURE BLOCKCHAIN & ECOSYSTEM FOR ECOMMERCE AND DIGITAL ADVERTISING]

## WARNING

We are still working on the interface and know there are still a number of bugs and cross browser issues - please be patient.. in the meantime please use our original [captcha UI code from here](https://github.com/JSEcoin/server/tree/master/embed/captcha).

## Overview
JSE Captcha is a free to use bot prevention tool. It can be used to protect content and endpoints from automated requests.

Official Release and Developer docs acan be found here: https://developer.jsecoin.com

Setting up the captcha requires two parts, a code snippet on the web page and then a server-side verification check.

Server-side Verification
It is essential to check the captcha has been completed using server-side code to protect your endpoints. We do this using the clients IP address (IPV4) and the following URL: 

```
https://api.jsecoin.com/captcha/check/:ipAddress/
```

## Demo
[Demo](https://jsecoin.com/iCaptcha/).

PS.. Check out our live [Platform](https://platform.jsecoin.com/).

## Technology:

JSE Captcha has been built with [Svelte](https://svelte.dev).

Svelte is a radical new approach to building user interfaces. Whereas traditional frameworks like React and Vue do the bulk of their work in the browser, Svelte shifts that work into a compile step that happens when you build your app.

Instead of using techniques like virtual DOM diffing, Svelte writes code that surgically updates the DOM when the state of your app changes.

### 1. Re-use in Svelte Apps
```html
<script>
  import JSEcaptcha from 'JSEcaptcha.svelte';
</script>

<JSEcaptcha theme="flat" size="M" on:success="{() => console.log('On success!')}" on:fail="{() => console.log('On fail!')}" />
```

### 2. All other Apps / Sites can use IIFE:

IIFE build:

```html
<script src='/jsecaptcha.iife.min.js'></script>

<div id="captcha"></div>
```

Add component:

```javascript
var jseCaptcha = new Jsecaptcha({
    target: document.getElementById('captcha'), //injection point
    props: {
        size: 'S', // ['','S','M','L']
        theme: 'flat', //['','flat']
        //captchaServer: 'https://load.jsecoin.com', //just for JSE devs
    }
});

//success response
jseCaptcha.$on('success', (res) => {
    console.log('Success: ', res.detail);
});

//failed reponse
jseCaptcha.$on('fail', (res) => {
    console.log('Fail: ', res.detail);
});
```

## Properties

- **size** controls the UI display
  - 'S' - Small
  - 'M' - Medium
  - 'L' - Large
- **theme** available themes
  - '' - dropshadow popup theme
  - 'flat' - flat simple theme
- **captchaServer** only used by devs for testing tweaking server side algorithms.
  - url of server (https://load.jsecoin.com)

## Events

- **success** - Emitted if user passes captcha bot detection tests.
- **fail** - Emitted if user fails captcha bot detection tests.

## Event Response (JSON)

#### Success
```json
{"success":1,"rating":87,"pass":true,"knownIP":true, "ip":"148.252.129.187"}
```

#### Fail
```json
{"success":1,"rating":0,"pass":false,"knownIP":false, "ip":"148.252.129.187"}
```

## Developers
### Quickstart

1. Install [Node.js](https://nodejs.org) v8.0.0 or higher.
2. Clone this repository: `git clone https://github.com/JSEcoin/captcha`
3. Install dependencies `npm install`

### Init dev environment

```bash
npm run dev
```

Open browser to http://localhost:5000

### Build

```bash
npm run build
```

Open /dist folder to locate build assets


## Bug Bounty
This is an initial push alot of cleanup is still required if you spot an issue please report it and if we consider it a major issue we will credit your account as part of our bug bounty offering.
[Bug Bounty Info Page](https://jsecoin.com/en/oddJobs/bugBounty)

## Contribute
If you'd like to assist and help the team please first review our [Contribution Guidelines](./CONTRIBUTING.md).

## Credits
The component was originally created from the component project template by Yogev: https://github.com/YogliB/svelte-component-template
And extended to support ie11 with this approach https://github.com/angelozehr/svelte-example-museums - https://blog.az.sg/posts/svelte-and-ie11/ by Angelo

## License
This project is under the [GNU General Public License v3.0](./LICENSE.md).


[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2FAremixdj%2Fcaptcha.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2FAremixdj%2Fcaptcha?ref=badge_large)