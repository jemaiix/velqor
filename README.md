<p align="center"><img src="assets/velqor-logo.svg" alt="Velqor" width="320"></p>

# Velqor

A single-page workout, cardio and nutrition tracker. No build step, no backend — open `index.html` and it works.

## Features
- Strength logging with set-by-set workouts, weight steppers, repeat-last-set and a rest timer with suggested breaks
- Custom workouts, a weekly plan, a generator for training weeks and ready-made programs
- Cardio and other sports logging (calories estimated from MET values), quick logging of single exercises or cardio from the Workout tab
- Food diary with a macro database, your own products, and daily/weekly/monthly macro pie charts
- Workout history, records, weekly summary and period statistics
- Shareable summary image with your own background photo
- Finnish, Swedish and English
- Installable on your home screen with the Velqor icon (iOS: Share → Add to Home Screen; Android: install prompt) and a share button; works offline after the first visit

## Running it
Open `index.html` in a browser, or serve the folder (`python3 -m http.server`).
To publish with GitHub Pages: **Settings → Pages → Deploy from a branch → `main` / root**.

## Home screen app
The repo includes `manifest.webmanifest`, `sw.js` and the icons in `assets/` (`apple-touch-icon.png`, `icon-192.png`, `icon-512.png`, `icon-512-maskable.png`). The install button appears on phones when the site is opened in a normal browser tab over HTTPS (GitHub Pages is fine). If you change `index.html` and don't see updates, bump `V` in `sw.js`.

## Rest-timer sound and notifications
The rest timer plays a three-tone chime using Web Audio in the *ambient* audio session, so music from Spotify or Apple Music keeps playing (the iPhone silent switch mutes it). During a workout the screen is kept awake. If you allow notifications (installed home-screen app only on iOS), a notification is shown when a rest ends while the app is in the background. Browsers freeze background pages, so on iPhone this works only while the app is still running; a reliable alert while the app is closed would need a push server or a native app.

## Push alerts when the app is closed (ntfy)
Browsers freeze background pages, so a web app cannot fire a timer notification while it is closed. Velqor therefore schedules the alert on a push service when a rest starts: **Profile → Rest alerts**. Turn it on, install the free [ntfy](https://docs.ntfy.sh/subscribe/phone/) app, subscribe to the private topic shown there, and press *Send test*.
- The app posts a delayed message (`delay`) to `https://ntfy.sh` (or your own ntfy server, editable in the settings). The message text is generic; the topic name is a random secret, so keep it private.
- Pausing, skipping, stopping or adjusting the timer cancels or re-schedules the message (`DELETE /<topic>/<sequence_id>`). When the app is open, the in-app chime plays instead and the push is cancelled just before it fires.
- The delay must be at least 10 seconds. Delivery depends on iOS/Android notification settings for the ntfy app.
- This only works on your own site (GitHub Pages), not inside Claude, because Claude's page blocks requests to other sites.

## Your data
Everything is stored in your browser's `localStorage` on the device you use. Clearing site data deletes it, and it is not synced between devices.

## Photo features
Meal photo estimates, package label reading and exercise recognition from photos use Claude and only work when the page is hosted in Claude. On GitHub Pages these buttons show a message and the rest of the app works normally. Doing this standalone would need a backend that holds an API key; never put an API key in client-side code.

## License
Not chosen yet — add a `LICENSE` file before sharing the code.
