# Marquee Router — installing on your Android phone

This folder is a Progressive Web App (PWA). It behaves like a real installed
app — its own icon, full-screen with no browser bar, works offline — but it
installs straight from a webpage instead of the Play Store.

**Important:** installing to the home screen only works if these files are
served over `http://` or `https://`. Opening `index.html` directly from a
`file://` link (e.g. double-tapping it in a file manager) will *not* let you
install it — Android requires a real web address for that part.

## 1. Host the folder somewhere (pick one, all free)

**Easiest — GitHub Pages**
1. Create a free GitHub account if you don't have one.
2. Create a new repository, upload all the files in this folder to it
   (`index.html`, `manifest.json`, `sw.js`, the three `.png` icons).
3. In the repo's Settings → Pages, set the source to your main branch.
4. GitHub gives you a URL like `https://yourname.github.io/repo-name/`.

**Also easy — Netlify Drop**
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. It gives you a live URL immediately, no account required for a quick test
   (create a free account if you want the link to stay permanent).

**Also fine — Vercel, Cloudflare Pages, or any static host** work the same way:
upload the folder, get a URL back.

## 2. Install it on your phone

1. Open the hosted URL in **Chrome** on your Android phone.
2. Tap the **⋮** menu in the top right.
3. Tap **"Install app"** (or **"Add to Home screen"** — wording varies by
   Chrome version).
4. Confirm. An app icon appears on your home screen / app drawer.

From then on, tapping that icon opens Marquee Router full-screen, like any
other installed app. Your saved plan and pinned lineup (from the Save Plan /
Save Lineup buttons) live in that browser's local storage, so they'll be
there the next time you open the app too.

## Notes

- **Offline use:** the service worker (`sw.js`) caches the app itself, so it
  still opens without a signal. The Google Maps auto-fill feature still
  needs an internet connection when you use it, same as before.
- **Updating later:** if you edit `index.html` and re-upload, phones that
  already installed the app will pick up the change automatically the next
  time they open it with a connection (the service worker checks for
  updates in the background).
- **This is not a Play Store app.** There's no APK and nothing to submit to
  Google — it's a bookmark that looks and feels like an app. If you
  eventually want an actual installable `.apk` (e.g. to side-load without
  hosting anywhere, or to publish on the Play Store), the standard next step
  is running this same folder through **PWABuilder** (https://pwabuilder.com) —
  paste your hosted URL in and it packages an Android APK for you. That step
  needs to happen outside this chat since it requires a live hosted URL.
