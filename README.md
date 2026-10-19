# ShiftFit Adaptive Dashboard

A mobile-friendly, shift-aware training dashboard built as a static GitHub Pages site. The published repository contains its app shell, generic workouts, and dated workout-template assignments—not private Health measurements, body metrics, work shifts, or personal calorie targets.

## Site and publishing

Repository: https://github.com/JacZerin24/health-and-fitness-plan  
Expected project URL: https://jaczerin24.github.io/health-and-fitness-plan/

The GitHub Actions workflow at `.github/workflows/pages.yml` deploys on every push to `main`. In repository **Settings → Pages**, select **GitHub Actions** as the publishing source. Check the **Actions** tab and Pages settings for deployment status; a workflow file alone does not enable Pages.

## How to use

1. Open the site on your own device. The published site starts with generic strength/cardio programming and no personal metrics or shifts.
2. Open **Data & sync → Import JSON** and select your private ShiftFit refresh/backup file. Partial refresh files **merge** into existing local data instead of erasing workouts, history, or older future shifts.
3. Use **Schedule** to adjust individual shift dates or import an updated Google Calendar `.ics` export. The shift code date is the event's local start date.
4. Use **Progress → Log progress** for a new weight/waist measurement. An old weight is labeled as last recorded, not assumed current.
5. Export a browser backup before changing devices or clearing site data.

## Data freshness

Apple Health and Google Calendar **do not sync automatically** through GitHub Pages. A ChatGPT Health refresh can be prepared as a private JSON file and imported locally. Charts show the last imported completed-day data; sleep-based workout adjustments only apply to fresh snapshots (within two days). Older data is displayed for context, not used for an immediate readiness judgment.

Private data is stored in your browser's `localStorage`. Data does not sync between devices, and using private/incognito mode or clearing browser storage will remove it. The private JSON itself must stay out of the repository.

## Privacy and history

The former `data.json` in this repository contained personal data. The current version removes that content from the **latest branch and deployed site**, but earlier Git commits may still retain it. Rewriting history or recreating a repository would be needed to remove that historical exposure. Do not commit private backups, Apple Health exports, shift-calendar exports, tokens, or private feed URLs.

See [DATA_FORMAT.md](DATA_FORMAT.md) for import schema.
