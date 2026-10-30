# rainshadowhealth.org

The Rainshadow Health Innovation site. Eight static files, no build step, no dependencies. Open `index.html` in a browser and it runs.

Rainshadow is Oregon's statewide convener for health technology, built on the model New Mexico proved, and incubated by [Builders VC](https://builders.vc/). Its flagship is the Health ACCORD Challenge. Sibling to [waystation-site](https://github.com/BDO811/waystation-site), which is the delivery company behind the rural pilots.

| File | Role |
|---|---|
| `index.html` | home, with the Cascade cross section drawn on a canvas |
| `accord.html` | the Health ACCORD Challenge |
| `priorities.html` | the opening Oregon priorities |
| `apply.html` | for health technology companies |
| `about.html` | how it is built, the seats, who to approach |
| `tokens.css` | palette, type scale, spacing |
| `base.css` | element defaults |
| `style.css` | page rules |
| `robots.txt` | opens the site to crawlers and points at the sitemap |
| `sitemap.xml` | the five pages, for search engines |

## Nobody in Oregon has agreed yet

Rainshadow itself is set up and incubated by Builders VC, and the site says so in the present tense. What is not settled is the Oregon side: every organisation named on the About page is a counterpart to approach, not a partner, and none has been approached. Every page carries that sentence in its footer and the deploy workflow refuses to publish a page that has lost it.

The site is open to search engines as of 30 October 2026. `robots.txt` allows everything and names the sitemap, no page carries a `noindex` tag, and each one declares a canonical URL on the apex so the apex and `www` are not credited separately.

**To close it again:** put `Disallow: /` back in `robots.txt` and add `<meta name="robots" content="noindex, nofollow">` to the five pages. The workflow checks that robots.txt and the meta tags say the same thing in either direction, so a half-done change in either direction fails the deploy rather than leaving the site indexed in pieces.

## Nothing confidential goes in here

This repo is public, because that is what makes Pages free. The canon, the clearance run, the investment materials and anything naming a customer, a partner or a certification stay in the private `claude-outputs` repo and in Google Drive.

## Deploying

Every push to `main` publishes. The workflow refuses to deploy when a file is missing, when a page no longer says that no Oregon organisation has agreed, when `robots.txt` and the meta tags disagree, when the site is open with no sitemap, or when a banned entity appears in the source.

Pages enables itself on the first successful run, so there is nothing to switch on by hand.

## DNS

`CNAME` in this repo claims the apex domain. The domain is registered with Squarespace, so the records change in Squarespace DNS and the registration stays where it is.

Apex `rainshadowhealth.org`, four A records:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

And `www` as a CNAME to `bdo811.github.io`.

Delete the Squarespace parking records for the apex at the same time, or the domain keeps resolving to the parking page. Pages issues the certificate once DNS resolves; turn on Enforce HTTPS after it does.
