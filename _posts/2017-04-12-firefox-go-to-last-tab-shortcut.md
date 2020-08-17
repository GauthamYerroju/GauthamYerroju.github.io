---
date: '2017-04-12 04:53 -0700'
last_modified_at: '2017-04-12 05:31 -0700'
published: true
title: 'Firefox: Go to last tab shortcut'
categories:
  - Customization
  - Tips
tags:
  - browser
  - firefox
  - shortcuts
  - workflow
---
In Firefox (and indeed most web browsers), CTRL + TAB moves us through open tabs (and CTRL + SHIFT + TAB moves us backward). When working with upward of a dozen tabs (which is not uncommon these days), if we need to switch between two tabs which are not adjacent, Firefox's default behavior requires us to use the mouse to switch between the two tabs or to cycle through all the tabs in between. I ran into this situation often enough to make me look for an ALT + TAB type behavior: switch to last tab. Turns out, there's a flag for that.

Navigate to the [about:config](about:config) page, look for the flag __browser.ctrlTab.previews__ and set it to __true__.

Now, CTRL + TAB will have the same behavior as ALT + TAB, complete with previews:
![Tab previews](/img/post-images/2017-04-12-firefox-go-to-last-tab-shortcut/tab-previews.png)

Enjoy!
