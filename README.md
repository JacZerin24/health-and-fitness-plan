# ShiftFit Adaptive Dashboard

A privacy-conscious static dashboard for a rotating-shift fitness/body-recomposition plan. It is designed to run on GitHub Pages without committing private Apple Health, work-calendar, body metrics, nutrition targets, or dated personal plan data to the repository.

## What it does

- Generates the current week from an imported shift pattern instead of fixed weekdays.
- Uses a private imported plan configuration for dated phases, calories, protein, steps, and cardio doses.
- Includes reusable Strength A/B/C workouts, minimum-viable workouts, recovery logic, and overnight-shift rules.
- Lets the user import recognized work shifts from a Google Calendar `.ics` export or edit individual days.
- Stores imported schedule, plan configuration, Apple Health summary metrics, and weight history only in browser `localStorage`.
- Exports/imports a private JSON backup.
- Works offline after first load via a basic service worker.

## Privacy

Do **not** commit a private starter/backup JSON, raw health export, Google Calendar private feed URL, `.ics` export, or OAuth token. GitHub Pages is a static host and browser code is visible to visitors. This repository contains only the app shell and generic workout/recovery logic.

The `.gitignore` intentionally excludes common private-data filenames.

## Deploy on GitHub Pages

Repository: `JacZerin24/health-and-fitness-plan`

1. Put these files on the default `main` branch.
2. In **Settings → Pages**, set the source to **GitHub Actions** if it is not already selected.
3. The included workflow deploys the site on every push to `main`.
4. Open the deployed site and import the private starter JSON locally.

## Updating a changing schedule

- Click an individual day in **Schedule** and change its shift; or
- Export/import a fresh Google Calendar `.ics` file. The importer recognizes titles such as `[LIX] G Shift (6am-2pm)`.

A fully automatic private Google Calendar sync would require a secure backend/OAuth arrangement. Credentials are intentionally not embedded in a public GitHub Pages app.

## Updating Apple Health

Web browsers cannot read iPhone HealthKit directly. Import a refreshed private JSON snapshot generated from connected Health data, or log the decision-driving metrics manually. Sleep and shift transitions can downgrade training; HRV/resting HR are displayed as context rather than converted into a medical or readiness score.
