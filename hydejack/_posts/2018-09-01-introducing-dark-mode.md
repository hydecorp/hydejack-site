---
layout: post
title: Introducing Dark Mode
image: 
  path: /assets/img/blog/steve-harvey.jpg
  srcset:
    3000w: /assets/img/blog/steve-harvey.jpg
    1500w: /assets/img/blog/steve-harvey@0,5x.jpg
    750w:  /assets/img/blog/steve-harvey@0,25x.jpg
    375w:  /assets/img/blog/steve-harvey@0,125x.jpg
description: >
  The PRO version of Hydejack now includes an optional Dark Mode, making it the first Jekyll theme to include this feature.
---

Like many people, I'm a sucker for dark UI themes, whether it's Twitter, macOS, or code editors. I even [built an addon for Atom](https://atom.io/packages/theme-flux-solar) that automatically switches between light and dark based on sunset and sunrise.

When I was playing around with Unity, I even considered a subscription just so I could use the dark theme, which is exclusive to subscribers. Following this line of thought, I've added a Dark Mode to the PRO version of Hydejack.

![Dark Mode](/assets/img/blog/dark-mode.jpg){:width="1440" height="836"}
*This is what it looks like!*
{:.figure}

A unique challenge with regards to Hydejack was its color customization feature. As it turns out, a generic gray does not look good when combined with many accent colors, while a slightly tinted gray only looks good with a small range of accent colors.

To solve the problem, Hydejack's Dark Mode adjusts the background based on the `theme_color`. This property can be set for the entire site, or individual pages just like `accent_color`. It also adjusts the UI of many browsers that support the Web App Manifest API, making the whole experience even more seamless.

![Adaptive Dark Mode Example](/assets/img/blog/dark-mode-ii.jpg){:width="1440" height="836"}
Dark Mode adjusts to a different accent colors.
{:.figure}

While it's not feasible to enable Dark Mode based on a visitor's exact sunrise and sunset times[^1], site authors can opt-in to enable Dark Mode based on a visitor's local time.

Site authors can also enable Dark Mode by default and/or hide the light switch:

```yml
hydejack:
  dark_mode:
    # Set to `true` to always use the dark theme.
    always:            false

    # Set to `true` to use the dark theme based on visitors' local time.
    dynamic:           true
    sunrise:           6
    sunset:            18

    # Set to `true` to allow visitors to switch between light and dark mode.
    icon:              true
```

Dark Mode is now available for buyers of the [PRO version][buy].

[buy]: https://buy.polar.sh/polar_cl_CczddJM50iZgR_iuUhc_54RcSg1KasTEJtOSqTvlpUI

<script type="module">
  const classes = document.body.classList.toString();
  document.body.classList.add('dark-mode');
  document.querySelector('hy-push-state').addEventListener('after', () => setTimeout(() => document.body.setAttribute('class', classes), 700), { once: true });
</script>

[^1]: This would require visitors' permission to read their geolocation, which is not reasonable or practical for this use case.
