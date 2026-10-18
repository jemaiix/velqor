<p align="center"><img src="assets/velqor-logo.svg" alt="Velqor" width="320"></p>

# Velqor

A single-page workout, cardio and nutrition tracker. No build step, no backend — open `index.html` and it works.

## Features
- Strength logging with set-by-set workouts, weight steppers, repeat-last-set and a rest timer with suggested breaks
- Custom workouts, a weekly plan, a generator for training weeks and ready-made programs
- Cardio and other sports logging (calories estimated from MET values), Apple Health workout import (`export.zip`)
- Food diary with a macro database, your own products, and daily/weekly/monthly macro pie charts
- Workout history, records, weekly summary and period statistics
- Shareable summary image with your own background photo
- Finnish, Swedish and English

## Running it
Open `index.html` in a browser, or serve the folder (`python3 -m http.server`).
To publish with GitHub Pages: **Settings → Pages → Deploy from a branch → `main` / root**.

## Your data
Everything is stored in your browser's `localStorage` on the device you use. Clearing site data deletes it, and it is not synced between devices.

## Photo features
Meal photo estimates, package label reading and exercise recognition from photos use Claude and only work when the page is hosted in Claude. On GitHub Pages these buttons show a message and the rest of the app works normally. Doing this standalone would need a backend that holds an API key; never put an API key in client-side code.

## License
Not chosen yet — add a `LICENSE` file before sharing the code.
