---
title: 'The Why and How of Screen Reader Testing'
subtitle: Getting Started With Screen Readers
date: 2018-11-08 00:10:00
description: Blog post on why you should start testing your code with screen readers.
featured_image: '/images/blog/screenreader/Lead.jpeg'
---

Originally posted on [ThatBlog](https://medium.com/that-conference/the-why-and-how-of-screen-reader-testing-8a92add2a609). 

When I first started testing with a screen reader in 2015, I thought it was going to be nearly impossible. I started by opening the [Apple VoiceOver](https://www.apple.com/voiceover/info/guide/_1131.html) guide and tried to memorize the first ten (of many) shortcuts. I looked at [JAWS](https://www.apple.com/voiceover/info/guide/_1131.html), hoping for a simpler solution. Not only did it not work for my Mac, but it was also going to set me back over a thousand dollars. I couldn't see how this much effort was worth it for (what I thought was) only a few users. I was wrong.

One in five users in the United States has a legally recognized disability. This number does not include users with temporary impairments or those who have not reported a disability. If you’ve never seen someone with a screen reader on your analytics, it doesn’t mean they aren’t there. Analytics does not track assistive technologies screen readers, because screen readers read browsers themselves.

Creating for inclusion enables humans with unique experiences and all backgrounds to use your website or app. You increase your potential market share and protect yourself against lawsuits. Designing for voice assistance also means you get built-in SEO and easier integration with chat assistants (Alexa, Cortana, Siri, etc.) for minimal additional cost.

>“We design to embrace the things that make us human. It’s what drives us to create a world that makes lives better. The result is technology that’s inclusive.” —&nbsp;Microsoft

This article will cover basics of screen readers on desktops. [Android](https://support.google.com/accessibility/android/answer/6006564?hl=en) and [iOS](https://www.apple.com/accessibility/iphone/) both have a number of accessibility features built-in, including screen readers.

## How Screen Readers Work

Screen readers “read” both the structure and the text of elements on a page. Never label something like a button as “button” because the screen reader is intelligent enough to read that part to the user already. Don't use “Click Here,” “Tap to Continue” and similar labeling schemes that presume a specific action. A user could be using a mouse (clicking), their fingers or a stylus (tapping), a keyboard without a mouse (tab, key, press), a screen reader or any other assistive technology. Focus on the “what,” not on the “how.”


```html
<button>Save</button> is read as: Button, Save
<button>Save Button</button> is read as: Button, Save Button
```

All commonly used screen readers rely on a modifier key to access screen reader functionality while not overriding other keyboard shortcuts built into the browser or operating system. `Caps Lock`, `Command`, `Control` or several keys pressed at once are the most frequent modifier key combinations. The tutorials below assume you’ve got the default unique key enabled (`Insert` for NVDA, `Control + Alt` for VoiceOver). I personally have switched mine to `Caps Lock`, as that’s a key that I use less frequently. Experiment and figure out what works for you.

---

![Photo of NVDA](/images/blog/screenreader/NVDA.png)

## Testing on Windows

For Windows users, I recommend [downloading NVDA](https://www.nvaccess.org/download/). It’s entirely free to download, with an optional donation to help support continued improvements. NVDA officially supports Internet Explorer, Edge, Firefox and Chrome.

Once you’ve installed NVDA, you can open the program by pressing `Control + Alt + N`. To mute NVDA at any time press Control, or completely close it with `Insert + Q ` and then Enter.

In 2016, Heydon Pickering [surveyed individuals](http://www.heydonworks.com/article/responses-to-the-screen-reader-strategy-survey) who use screen readers and found that navigating by headings was the most used feature, whether by specific heading levels or general header navigation. With NVDA, you can simulate this behavior by navigating by heading or trying to reach a specific heading. Selecting the letter `H` will take you to the next heading (of any level).

>“I usually try to find a heading and then go from there. Usually, I do this by pressing the #1 or #2 on the keyboard, since the hope is that a competent web developer coded the site and that headings are where and at the level they should be” -&nbsp;Survey&nbsp;Respondent 

It’s crucial to nest your headings correctly because screen reader users rely heavily on the ability to jump directly to a heading level. If a website is written with correctly nested headings, you can skip navigating through every heading, and instead use `[1–6]` to jump directly to the next heading of that level.

Once you’ve found the area you’re looking for, you can use `Insert + Down Arrow` to start reading from the current position or `Control + Left/Right Arrow` to read the previous/next word.

Sometimes screen readers get words wrong. A word might have multiple meanings (Polish: People from Poland, Polish: To shine) or an abbreviation might be misinterpreted (No. 3 is read as “No Three”, not “number 3”). When this happens, users will direct the screen reader to read one character aloud at a time and then figure out the word themselves. To navigate by character, just use your `left and right arrows`.

NVDA uses a different mode for filling out forms. Like with headings and `H`, you can select `F` to jump past all other text and get to the next form field. Often, the first form field is a search box. Some NVDA users will start by pressing “F” right away and going to the search.

>“If I’m looking for a search facility, I’ll use the screen reader shortcut for moving to the first form field on the page” -&nbsp;Survey&nbsp;Respondent

If you want to be able to enter text into a form field, such as a text box, you’ll need to select form mode, which is `Insert + F`. Form mode allows you to enter text. Otherwise, NVDA will just keep using the single key shortcuts to navigate around the page. To exit form mode, use `Select + F`.

And those are the basics of NVDA! Unlike VoiceOver or JAWS, NVDA doesn’t have custom focus styling, which is why you still need to include a :focus element for your keyboard users. Once you’ve got those down, check out NVDA application and advanced navigation modes.

### Shortcuts at a Glance
* Open NVDA: `Control + Alt + N`
* Close NDVA: `Insert + Q` and then `Enter`
* Stop talking: `Control`
* Move to next element: `Tab` or `Shift + Tab` (back)
* Skip to next heading: `H`
* Skip to next form field: `F`
* Go to a specific heading level: `[1–6]`
* Read from current position: `Insert + Down Arrow`
* Read next/previous word: `Control + Left/Right Arrow`
* Read next character: `Left/Right Arrow`

This tutorial is based on NVDA Version 2018.3.2.

---

![Photo of VoiceOver](/images/blog/screenreader/VO.png)

## Testing on macOS

macOS users have a pretty powerful screen reader built in for free, VoiceOver. To access VoiceOver, Go to `System Preferences > Accessibility > VoiceOver`. Once VoiceOver is enabled, you can also use the TouchID on newer MacBooks to open it quickly. macOS includes a great built in tutorial for VoiceOver, which I also recommend watching.

VoiceOver does not have multiple modes like NVDA, instead relying on more complex shortcuts instead of single keys. The key combinations can end up quite a bit long, so you can use `Control + Option + —` to “lock” or “unlock” the keys to be just VoiceOver. For each of the commands, I’ll keep including `Control + Option` but locked keys will not have to keep including them.

To navigate between elements, users can always tab by link or element, but that can take a long time and not everything is always keyboard accessible. Many users leverage VoiceOver’s rotor. The rotor traverses the page using DOM elements, including tables, frames, images, headings, links and form controls. To open the rotor, use `Control + Option + U`. Once in the rotor, use left and right arrows to navigate through the element lists. Then, you can press the associated key to jump to that element. You can close the rotor at any time with `Escape`.

The rotor allows users to move incredibly quickly through a screen when the code is structured correctly. When headings are not properly nested or elements not correctly tagged, they do not appear in the rotor.

### Shortcuts at a Glance
* Open VoiceOver: `Command + Function + F5` (F5 will be on the touch bar if you have one)
* Close VoiceOver: `Command + Function + F5` (F5 will be on the touch bar if you have one)
* Click on an item: `Control + Option + Space`
* Lock to just VoiceOver: `Control + Option + —`
* Stop speech: `Control`
* Move to next element: `Tab or Shift + Tab (back)`
* Skip to next link: `Control + Option + Command + L`
* Skip to next heading: `Control + Option + Command + H`
* Open rotor: `Control + Option + U`
* Close rotor: `Escape`

Tested using VoiceOver on macOS High Sierra.

---

## A Note on ARIA
ARIA stands for Accessible Rich Internet Applications. ARIA is designed to make elements more semantic and easier for screen readers to understand. HTML5 brought incredibly useful semantic elements like `<nav>`, `<figure>`, `<header>`, `<footer>`, and `<summary>`, but developers occasionally still need to rely on custom ARIA tags for complex systems or code that is not updated to HTML5.

ARIA labels and roles alter how the DOM is traversed. In VoiceOver’s rotor, they end up in completely separate lists, making it easier for users to access. Looking into ARIA Techniques will help you design for screen readers and make your code more understandable to new developers on the project. Mozilla has a fantastic [write up on leveraging ARIA](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics), with a lot of useful code examples.

---
In 2017, plaintiffs filed at least 814 federal lawsuits about inaccessible websites. In 2018, this number is expected to rise to more than 2,000. As accessibility lawsuits rise, so does the need for accessibility skillsets. Leveraging screen readers is an essential part of that.

Accessibility is not the responsibility of one interested developer. It’s an ongoing conversation that belongs within the entire organization. Taking small steps, like learning how to use a screen reader, enables you to start crafting more meaningful and inclusive experiences for your entire audience.

>“Our hope is that by building more accessible products, we can make a meaningful difference in the lives of people around the world.” —&nbsp;Google

## Additional Resources
And that’s it! When starting, feel free to use a screen reader alongside a mouse. As you gain more familiarity with screen readers, try using just the keyboard. I’ve included a bunch of links below pointing to screen readers, NVDA, VoiceOver and general accessibility guidelines.

### All Screen Readers
* [Responses to the screen reader strategy survey](http://www.heydonworks.com/article/responses-to-the-screen-reader-strategy-survey)
* [Screen reader demo for digital accessibility (video)](https://www.youtube.com/watch?v=dEbl5jvLKGQ)

### NVDA (Windows only)
* [Download NVDA](https://www.nvaccess.org/)
* [WebAim: Getting started with NVDA](https://webaim.org/articles/nvda/#quick)
* [Google Chrome Developers: NVDA A11ycast (video)](https://www.youtube.com/watch?v=Jao3s_CwdRU)
* [NVDA complete list of commands](https://www.nvaccess.org/files/nvdaTracAttachments/455/keycommands%20with%20laptop%20keyboard%20layout.html)

### VoiceOver (Mac only)
* [WebAim: Using Voiceover to Evaluate Accessibility](https://webaim.org/articles/voiceover/)
* [Google Chrome Developers: VoiceOver A11ycast (video)](https://youtu.be/5R-6WvAihms)
* [VoiceOver complete list of commands](https://www.apple.com/voiceover/info/guide/_1131.html)

### General Accessibility
* [Accessibility check list](https://webaim.org/standards/wcag/WCAG2Checklist.pdf)
* [Microsoft inclusive design toolkit](https://www.microsoft.com/design/inclusive/)
* [A Web for Everyone](https://rosenfeldmedia.com/books/a-web-for-everyone/)