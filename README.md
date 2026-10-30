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
| `robots.txt` | keeps the site out of search while the entity is in formation |

## Nobody in Oregon has agreed yet

Rainshadow itself is set up and incubated by Builders VC, and the site says so in the present tense. What is not settled is the Oregon side: every organisation named on the About page is a counterpart to approach, not a partner, and none has been approached. Every page carries that sentence in its footer and the deploy workflow refuses to publish a page that has lost it.

The site is also closed to search engines, on purpose. `robots.txt` disallows everything and each page carries a `noindex` meta tag. The link works for anyone it is sent to; Google will not surface it. **To open the site up: delete `robots.txt` and remove the robots meta tag from the five pages.** The workflow checks that those two things stay in step, so a half-done change fails the deploy rather than quietly indexing the site.

## Nothing confidential goes in here

This repo is public, because that is what makes Pages free. The canon, the clearance run, the investment materials and anything naming a customer, a partner or a certification stay in the private `claude-outputs` repo and in Google Drive.

## Deploying

Every push to `main` publishes. The workflow refuses to deploy when a file is missing, when a page no longer says that no Oregon organisation has agreed, when `robots.txt` and the meta tags disagree, or when a banned entity appears in the source.

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
