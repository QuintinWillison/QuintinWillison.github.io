# www.qwuk.net

## Overview

This repository, specifically the [`docs` folder](docs/), contains the static source code for the website served at [www.qwuk.net](https://www.qwuk.net/).

The service being used to serve this site is [GitHub Pages](https://pages.github.com/).

The site is very simple at the moment and I'm not sure when I'll find the time to build it out more.
The important thing is that I got it started, right? :stuck_out_tongue_closed_eyes:

## GitHub Pages

I'm going to use this section to document my observations around the GitHub Pages technology.
This is as much for my own future self as for others who may also find them helpful.

### Missing Features

#### HTTP Redirects

Having used [Netlify](https://www.netlify.com/) quite a bit, one of the features I love about their offering is the support for the service responding with HTTP [`301` 'Moved Permanently'](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/301) and [`302` 'Found'](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/302) status codes (see [Redirects and rewrites](https://docs.netlify.com/routing/redirects/)). I notice that [GitLab](https://about.gitlab.com/) also support this (see [Create redirects for GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/redirects.html)).

This capability is sorely missing from GitHub Pages. This presents an issue for a couple of use-case scenarios which I wish the GitHub Pages team would consider supporting:

- **Sites moving** over to GitHub Pages from some other hosting situation where the previous technology being used was causing page addresses to need to have some kind of pollution in them (a.k.a. 'not pretty'). Now that these sites are moving over to GitHub Pages then there should be an opportunity for these paths to be cleaned up ('moved') without losing accumulated SEO juice (classic use-case for HTTP `301`).
- **Pages moving** within the GitHub Pages site once it's been established. Often we find that our originally anticipated folder structure doesn't fit purpose and we want to move things around. As for the previous point, an HTTP `301` fits the bill here.

It's worth noting that a form of redirect is possible using client-side-heavy hacks like the [Jekyll JekyllRedirectFrom plugin's `redirect_to`](https://github.com/jekyll/jekyll-redirect-from#redirect-to), but that this is invisible from an SEO perspective as ultimately the initial HTTP response is still [`200` 'OK'](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200).

### Troubleshooting

#### Location of the `CNAME` file

As [documented by GitHub](https://docs.github.com/articles/configuring-a-publishing-source-for-github-pages/), there is a choice from one of two possible directories that the published source can be located - either at root (`/`) or in `/docs`. The `CNAME` file must be located in this folder - i.e. it should be considered 'part' of the published sources.

You can see if the `CNAME` file is being picked up from the 'Pages' section in your repository's 'Settings'. In fact, the reality is that most people probably end up setting it from there - in which case GitHub commits it back to the repository on your behalf anyway.
