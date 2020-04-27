---
date: '2020-04-27 07:00 -0700'
last_modified_at: '2020-04-27 07:00 -0700'
published: true
title: 'CSS Reference: Display and Position'
categories:
  - Coding
  - Web Development
---
This is a quick reference for how CSS display and position properties work.

## Display

Elements are arranged from left to right, top to bottom. Display properties define how elements are treated when being placed in the flow.

### inline

- Aligns with baseline (as in, the baseline on which text is aligned)
- Margins and padding are only applied horizontally
- Will ignores width and height

### block

- Will not allow other elements to be on the same line (except "run-in" siblings)
- Width and height are respected

### inline-block

- Same as "block", but will allow other elements on the same line

### run-in

- Allows elements to be on the same line as a block element
- Can be used for things like this: <h1>T</h1><p>his is a title</p>

### flex

- The best resource there is: [CSS Tricks: A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

### grid

- The best resource there is: [CSS Tricks: A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

## Position

**Remember:** position property doesn't cascade!

### static

- The default value
- Left, right, top, bottom and z-index are ignored, decided by browser

### relative

- Element's position is relative to *itself*
- Overlaps static elements
- Left, right, top, bottom and z-index are respected
- L, R, T, B properties just nudge the element in its place

### absolute

- Remove element from flow and float it, relative to the nearest *relative* or *absolute* positioned ancestor

### fixed

- Same as absolute, but positioned relative to viewport instead of nearest *relative* or *absolute* positioned ancestor
