
# Spicy Readme Graphics

[<img src="https://github.com/bleafman/spicy-readme-graphics/raw/master/assets/spicy-graphic.gif" width="100%" alt="👋 Hi there! Welcome to (spicy-readme-graphics | https://github.com/bleafman/spicy-readme-graphics)" title="👋 Hi there! Welcome to (spicy-readme-graphics | https://github.com/bleafman/spicy-readme-graphics)"/>](https://github.com/bleafman/spicy-readme-graphics)

## What is this

Spicy Readme Graphics is a simple app with some cool effects to help people spice up their Github repos and profile pages. After spicing up my [my personal Github profile](https://github.com/bleafman/), I wanted to make a more general solution for use in the future and thought others might find it helpful.

## Should I have a Readme graphic

No idea. Companies always seem to be asking for a Github profile link, so it seems like a graphic would help make a good first impression.

Keep in mind that it increases the page load time and data requirement for your Github Readme (the GIF above is 3.5MB after optimization) so you may just want an image or maybe no graphic at all.

## How to use Spicy Readme Graphics

### Table of contents

- [A quick note before getting started](#a-quick-note-before-getting-started)
- [Prerequisites](#prerequisites)
- [Getting started](#getting-started)
- [Explanation of the files](#the-files)
- [Make it your own!](#make-it-your-own)
- [Making a screen recording](#making-a-screen-recording)
- [Turning the recording into a GIF](#turning-the-recording-into-a-gif)
- [Using Spicy Readme Graphics as a landing page](using-spicy-readme-graphics-as-a-landing-page)

### A quick notes before getting started

Spicy Readme Graphics intentionally uses a simple setup (just HTML, CSS, JS, mostly in a single file) and tries to expose everything that is going on so that someone with a basic introduction to HTML/CSS/JS can understand how it works.

I spend a fair amount of time on forums like [/r/webdev](https://www.reddit.com/r/webdev/) and often see new developers getting overwhelmed when there's too much abstraction.

Spicy Readme Graphics is intentionally less ergonomic than it could be in order to prevent obscuring/abstracting complexity (although I'm definitely open to any suggestions and improvements!).

### Prerequisites

You'll be OK using Spicy Readme Graphics if you have...

1. A basic understanding of HTML/CSS/JavaScript
2. A text editor like [VS Code](https://code.visualstudio.com/)
3. A basic understanding of git and Github (if you're reading this on Github then you're probably good to go)
4. A very basic understanding of the terminal
5. Know how to get an HTML file on your computer to show up in a browser

**AND/OR**

A willingness to use Google and figure stuff out as you go. Also known as ["technical sophistication"](https://medium.com/@jajoosam/technical-sophistication-d33a88650032).

### Getting started

1. Make [a fork](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo) of this repo.
2. [Clone](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository) the forked version to your computer.
3. Open the repo in your text editor.
4. Open the [index.html](./index.html) file a browser.

### The Files

The main file you'll be working with is [`index.html`](./index.html).

It has all the code for the text and particle effects starting where you see:

```html
    /***** MAKE YOUR CHANGES HERE *****/
```

which is currently on line `56`.

[`assets/css/main.css`](./assets/css/main.css) will let you change the text color, the font, and the background color (note that background color is normally overwritten by the particle effect background).

## Make it your own

In [`index.html`](./index.html) you'll find a comment:

```html
    /***** MAKE YOUR CHANGES HERE *****/
```

Below that comment are two things:

1. a [TypeIt.js](https://typeitjs.com/) instance (i.e. `new TypeIt(...some stuff here...)`)
2. a [tsParticles](https://github.com/matteobruni/tsparticles) instance (i.e. `tsParticles.load((...some stuff here...)`)

You can follow the recommendations in the comments on how to customize the page OR go to the links in the comments and read more about the tools and how to customize them (remember where I said you might need some technical sophistication? =P)

To recap the comments in the code:

1. For TypeIt, you can edit the strings inside of the `.type()` function and it will change what is typed.
2. For tsParticles, the second argument in `tsParticles.load()` is a config for what is going to be displayed. [Demo configs can be found here.](https://particles.matteobruni.it/Samples#preset) It's probably best to check out the demos, pick one you like, and then make adjustments to it.

### Making a screen recording

Before turning your awesome graphic into a GIF, you'll need to make a screen recording of it.

[Making a screen recording on Mac](https://support.apple.com/en-us/HT208721)
[Making a screen recording on PC](https://www.pcmag.com/how-to/how-to-record-the-screen-on-your-windows-pc-or-mac)

**NOTE** If you want to have an easy time turning your recording into a GIF, you'll want your final recording to be less than 15 seconds (more on this in the next section).

### Turning the recording into a GIF

There's two ways to do this:

1. EASY: Use GIPHY
2. ADVANCED: On your own via command line

#### Use GIPHY

GIPHY is really good at taking videos and turning them into optimized GIFs (not surprising for a company that has a LOT of GIFs).

If your video is less than 15 seconds, you can upload it to GIPHY, and then download it as an optimized GIF. I used the "Social" optimized version in the GIF at the top of the page.

#### Command Line

As you can imagine, this is going to require a lot more technical sophistication. I'd only recommend this if you REALLY need more than 15 seconds. Keep in mind that 15 seconds is a long time to look at a GIF and it's going to make your READMEs load much slower.

[Here's the info I used to convert a video to a GIF via command line here.](https://askubuntu.com/questions/648603/how-to-create-an-animated-gif-from-mp4-video-via-command-line).

I ended up installing `ffmpeg` and `imagemagick` and then ran the following command (`input.mp4` should be replaced with your video recording):

```
ffmpeg -i type-effect-video.mov -vf "fps=15,scale=480:-1:flags=lanczos" -c:v pam -f image2pipe - | convert -delay 5 - -loop 0 -layers optimize output-480.gif
```

That said, you probably shouldn't run things in terminal given to you by strangers on the internet unless you know what you're doing. The GIPHY approach is much better if none of this made any sense to you.

### Setting up the graphic on your README

If you inspect the Raw output for what you're reading right now, you'll see the following:

```javascript
[<img src="https://github.com/bleafman/spicy-readme-graphics/raw/master/assets/spicy-graphic.gif" width="100%" alt="👋 Hi there! Welcome to (spicy-readme-graphics | https://github.com/bleafman/spicy-readme-graphics)" title="👋 Hi there! Welcome to (spicy-readme-graphics | https://github.com/bleafman/spicy-readme-graphics)"/>](https://github.com/bleafman/spicy-readme-graphics)
```

After uploading your GIF to your Github repo, you'll want to copy change `https://github.com/bleafman/spicy-readme-graphics/raw/master/assets/spicy-graphic.gif` with the path to your gif. It should go something like this:

```
https://github.com/:your-github-profile/:your-github-repo/raw/master/:path/:to/:gif
```

### Using Spicy Readme Graphics as a landing page

This is a somewhat advanced topic. For a simple solution click this button and follow the steps:

<a href="https://app.netlify.com/start/deploy?repository=https://github.com/bleafman/spicy-readme-graphics"><img src="https://www.netlify.com/img/deploy/button.svg" alt="Deploy to Netlify"></a>

It will fork this repo and deploy it. You can then make changes to the master branch and they'll be live on the internet!
