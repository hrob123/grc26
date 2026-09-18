# For GRC

A birthday page. Single HTML file, no build step.

---

## 1. What you still need to write

Open `index.html` and find the block near the top of the `<script>` that says:

```
✎ EVERYTHING YOU NEED TO EDIT IS IN THIS BLOCK.
```

Everything below that, down to `↓ machinery`, is plain text you can change.

| What | Where | Status |
|---|---|---|
| The letter | `letter: [ ... ]` | **Drafted** - read it, make it yours |
| The vouchers | `vouchers: [ ... ]` | Done, your wording |
| The secret line | `secret:` | `[ WRITE HERE ]` - or delete it |
| Flight date | `countdownTo:` | `'2027-05-01'` - change when you book |

The letter is a first draft in your voice. Change anything that doesn't sound like
you - it should read like you wrote it at the kitchen table, not like it was
proofread.

Apostrophes: the letter and voucher text sit inside backticks (`` ` ``), so you can
type freely. In the shorter single-quoted lines you need `you\'re`, not `you're`.

## 2. Test it

Double-click `index.html`. Squash the window narrow, or press F12 and toggle the
device toolbar to see it as a phone.

## 3. Push it

```bash
git init
git add .
git commit -m "for grc"
git branch -M main
git remote add origin https://github.com/YOURNAME/REPONAME.git
git push -u origin main
```

Name the repo something she won't guess - the URL becomes
`yourname.github.io/reponame`. Something like `sept-twentyone`.

## 4. Turn Pages on

Repo → **Settings** → **Pages** → Source: `Deploy from a branch` → Branch: `main`,
folder `/ (root)` → **Save**. Wait 1-2 minutes; the URL appears on that page.

## 5. Before you send it

- Open it on your actual phone, not just the desktop preview.
- **Check the map draws.** See the map section below. If it's ever blank, the page
  falls back to a tappable list of the same places automatically.
- Tap through the whole thing once, start to finish.

---

## The map

**Your CARTO key is already in.** It sits on one line near the top of the `CONTENT`
block in `index.html`:

```js
mapKey : 'cb1_3pe0_1_5d6e45f2620989b6000fcf63',
```

Nothing else to do. To change or remove it later, edit that one line - blank it out
and the map falls back to OpenStreetMap on its own.

### How the map picks its tiles

It tries three sources in order and drops to the next one automatically if tiles
fail to load. You don't have to do anything; this is just so you know what you're
looking at:

1. **CARTO `dark_all`** with your key - a proper dark basemap, shown as-is.
2. **CARTO `voyager`** with your key - the URL CARTO emailed you. It's a light map,
   so the page flips it to dark with a CSS filter.
3. **OpenStreetMap** - no key, also flipped to dark.

If all three fail it prints *"Map tiles couldn't load on this network"* under the
map, and the pins still work.

I couldn't reach CARTO from where I built this, so I couldn't confirm `dark_all`
works with your key - hence the cascade. If it doesn't, you'll land on `voyager`
and won't notice anything wrong.

**Free tier:** 5 million tile requests per calendar month, non-commercial use. This
page will use a few hundred. There's no card on file, so nothing can charge you.

**The key will be visible** in the public repo. It's free, rate-limited and
replaceable, so it doesn't really matter - but if you ever want it gone, email
CARTO for a new one and swap that line.

### If the map is blank

It's almost always the network, not the page. Some office and corporate networks
block map tile servers. After four failed tiles the page now says so under the map,
and the pins still work regardless. Test it on your phone on mobile data before
assuming it's broken - that's the network Grace will be on.

If Leaflet itself fails to load, the whole map is replaced by a tappable list of
the same places automatically.

---

## What's in here

```
index.html      the whole page
img/            24 photos, 01-25 in date order (11 removed)
vendor/         Leaflet, the map library - bundled so it can't break
README.md       this
.nojekyll       stops GitHub messing with the folders
```

## Notes

- **It's a public repo.** The link is unguessable and search engines are blocked
  (`noindex`), but anyone with the URL can open it.
- **Two captions are hidden** behind a press-and-hold (9 May, 17 July). The
  Queen's Wharf story on the map is blacked out until she taps it. To un-hide a
  caption, delete `hide:true` from its line in `shots`.
- **The map** has three views. *Brisbane* is the eight city pins, *Everywhere* adds
  the mountains, Fingal and Cairns, *What's next* is Tieri, Heron Island, Vietnam,
  Thailand and Malaysia in gold. Pins are tagged `city:true` for the Brisbane view -
  don't filter by latitude, Cairns is north of Brisbane and sneaks in.
- **To change the hero photo** on the birthday screen, edit the two places that say
  `img/17.jpg` - one in the CSS, one at the very bottom of the script.
- **Triple-tap GRC** on the last screen for the secret line.
