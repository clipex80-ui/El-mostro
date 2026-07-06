# The File — install as an app on your phone

This isn't a Play Store app (that needs a full Android build toolchain and a
developer account), but this gets you the same result: an icon on your home
screen, full-screen, works offline, and remembers your progress and streaks
day to day.

## Fastest path — GitHub Pages (free, ~10 minutes, no coding)

1. Go to **github.com** and make a free account if you don't have one.
2. Click the **+** in the top right → **New repository**.
   - Name it anything, e.g. `thefile-app`.
   - Set it to **Public**.
   - Click **Create repository**.
3. On the new repo page, click **uploading an existing file** (or drag files
   in). Upload all 5 files from this folder:
   - `index.html`
   - `manifest.json`
   - `service-worker.js`
   - `icon-192.png`
   - `icon-512.png`
4. Click **Commit changes**.
5. Go to **Settings → Pages** (left sidebar).
6. Under "Build and deployment", set **Source: Deploy from a branch**,
   branch: `main`, folder: `/ (root)`. Click **Save**.
7. Wait about a minute, then refresh — GitHub shows you a live URL like:
   `https://yourusername.github.io/thefile-app/`
8. Open that link on your **phone**, in **Chrome**.
9. Tap the **⋮** menu → **Add to Home screen** (or you'll see an automatic
   "Install app" banner). Confirm.

You now have an app icon on your home screen. Opening it launches full-screen,
no browser bar, and it'll keep working even with no signal once you've opened
it at least once while online.

## Simpler, no-hosting option (fewer features)

If you just want it *now* without the steps above: open `index.html` directly
in Chrome on your phone, then **⋮ → Add to Home screen**. You get the icon and
full-screen window immediately. The only thing you lose without proper
hosting is the offline service worker cache — but your checkbox progress,
streaks, and history still save fine, since that part uses your phone's local
storage, not the internet.

## Turning it into an actual APK

Once your GitHub Pages link from the steps above is live, you can generate a
real, installable `.apk` file — no Android Studio, no coding — using a free
tool called **PWABuilder** (built by Microsoft specifically for this).

1. On any browser, go to **pwabuilder.com**.
2. Paste your GitHub Pages URL (e.g. `https://yourusername.github.io/thefile-app/`)
   into the box and click **Start**.
3. It scans your site's manifest, icons, and service worker and shows a score.
   Since this app already has all three set up correctly, you should see
   green checks across the board.
4. Click **Package for stores**, then choose **Android**.
5. Leave the defaults (package ID, app name, etc.) unless you want to change
   them, then click **Generate**.
6. Download the package — pick the **APK** option (not AAB — that format is
   Play-Store-only and needs separate signing; APK installs directly).
7. Transfer the downloaded `.apk` to your phone (email it to yourself, or
   just download it directly on your phone if you ran PWABuilder there).
8. Open the file on your phone. Android will ask to allow installing from
   this source the first time — allow it, then tap **Install**.

That's it — you now have a real APK with its own icon in your app drawer,
runs in its own window with no browser bar, and includes the animations and
sounds already built into `index.html`. It's what's called a "Trusted Web
Activity" — technically a thin native wrapper around your web app, which is
also exactly how a large share of real Android apps in the Play Store work.

This produces the app for your own phone (sideloading). Actually publishing
it to the Play Store is a separate process that requires a $25 one-time
Google Play developer account and their review process — let me know if you
ever want to go that far.

## What's saved automatically

- Today's checked tasks
- Your day-by-day history (last 60 days)
- Current streak + best streak (a "streak day" = every single box closed)

Tap **Reset all saved data** on the Stats tab if you ever want to start clean.
