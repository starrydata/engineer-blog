---
layout: post
title: "Setting Up Google Analytics GA4 on GitHub Pages with the Minima Template"
date:   2025-02-06 15:55:28 +0900
categories: [Google-Analytics, Github-Pages, Minima, Web-Development]
author: "Tomoya Mato"
---


# Setting Up Google Analytics GA4 on GitHub Pages with the Minima Template

Starrydata Engineering Blog is also hosted on GitHub Pages. We understand that readers might wonder why an article on this blog is discussing GitHub Pages; as we run our own site on this platform, we’ve encountered this issue and want to share our solution for updating Google Analytics to GA4 on Jekyll sites using the Minima theme.

In this post, we'll explain how to configure your GitHub Pages site—built with Jekyll and the Minima theme—to use Google Analytics GA4. Currently, the default code provided in Minima (version 2.5.1) is for Universal Analytics, so manual adjustments are required to properly implement GA4 tracking.


---

## Environment

- **Jekyll:** 3.10.0
- **GitHub Pages:** 232
- **Minima:** 2.5.1

For the latest versions available on GitHub Pages, please refer to the official page:
[GitHub Pages Versions](https://pages.github.com/versions/)

---

## The Issue

The Minima theme’s default Google Analytics snippet is located in `<project_root>/_includes/google-analytics.html` and currently contains the following code:

```html
<script>
if(!(window.doNotTrack === "1" || navigator.doNotTrack === "1" || navigator.doNotTrack === "yes" || navigator.msDoNotTrack === "1")) {
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', '{{ site.google_analytics }}', 'auto');
  ga('send', 'pageview');
}
</script>
```

This script is designed for Universal Analytics and does not work with GA4.

---

## The Proposed Fix

https://github.com/jekyll/minima/pull/835/files

A pull request (PR) on the Minima GitHub repository suggests updating the code to support GA4. The revised snippet is as follows:

```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id={{ site.google_analytics }}"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', '{{ site.google_analytics }}');
</script>
```

This new code asynchronously loads `gtag.js` and initializes GA4 tracking with your provided tracking ID.

---

## Steps to Apply the Changes

1. **Update the Template File**
   Open the file located at `_includes/google-analytics.html` in your project root, and replace the existing Universal Analytics code with the GA4 snippet shown above.

2. **Set the Environment Variable**
   As per the official [Minima instructions](https://github.com/jekyll/minima/tree/v2.5.1?tab=readme-ov-file#enabling-google-analytics), set the environment variable `JEKYLL_ENV` to `production` for the relevant repository on Github. This ensures that the Google Analytics snippet is correctly injected during the production build.

3. **Configure the Tracking ID in _config.yml**
   Add your Google Analytics tracking ID (in the GA4 format, e.g., `G-XXXXXXXXXXXXX`) to your `_config.yml` file as shown below:

   ```yaml
   google_analytics: G-XXXXXXXXXXXXX
   ```

4. **Build and Deploy**
   Push your changes to GitHub. Once the build completes on GitHub Pages, verify that your site is loading the new `gtag.js` script and that the tracking is functioning correctly (using your browser’s developer tools or Google Analytics real-time reports).

---

## Conclusion

While the current version of the Minima theme only supports the legacy Universal Analytics, you can manually apply the GA4 updates as described above. This workaround will enable GA4 tracking on your GitHub Pages site until an official release of Minima with GA4 support is available. By updating the template file, setting the proper environment variable, and configuring your `_config.yml`, you can ensure that your site's analytics are up to date.
