# Private data format

The application intentionally ships without personal targets, dated phases, schedule, or health values. Import those privately in the browser.

A starter/backup JSON can contain any subset of these top-level fields:

```json
{
  "version": 2,
  "profile": {
    "name": "Example",
    "startWeight": 190,
    "targetWeight": 175,
    "protein": 150,
    "commuteMin": 30
  },
  "plan": {
    "phases": [
      {
        "id": "phase1",
        "name": "Phase 1",
        "start": "2030-01-01",
        "end": "2030-01-31",
        "cal": 2200,
        "protein": 150,
        "steps": "7,000/day",
        "strength": 3,
        "cardio": ["steady", "steady"],
        "dur": "30–35 min",
        "steadyDose": "5 easy + 20–25 brisk + 5 easy",
        "mode": "cut"
      }
    ],
    "nutrition": {
      "proteinRange": "140–160 g",
      "fatRange": "60–75",
      "fiberRange": "25–35",
      "hydration": "2–3 L/day baseline"
    }
  },
  "scheduleRanges": [
    {"start":"2030-01-02","end":"2030-01-03","code":"G"}
  ],
  "scheduleOverrides": {},
  "weightEntries": [
    {"date":"2030-01-05","weight":188.8,"waist":34.5}
  ],
  "health": {
    "snapshotDate":"2030-01-05",
    "latestSleepHours":7.8,
    "sleep7d":7.5,
    "steps7d":7200,
    "rhr7d":65,
    "hrv7d":40
  },
  "meta": {
    "scheduleStart":"2030-01-02",
    "scheduleThrough":"2030-02-01"
  }
}
```

## Shift codes

- G: 6 AM–2 PM
- I: 8 AM–4 PM
- X: supernumerary / usually daytime
- K: 10 AM–6 PM
- M: 12 PM–8 PM
- P: 2 PM–10 PM
- R: 4 PM–12 AM
- W: 10 PM–6 AM
- A: 12 AM–8 AM
- OFF: explicitly off
- TBD: schedule not loaded yet

## Calendar imports

The `.ics` importer looks for event summaries containing `[LIX]` followed by a recognized shift code and `Shift`. The earliest/latest recognized shift dates update known schedule coverage. Dates inside that coverage without a shift event are treated as off days. Dates after known coverage are shown as `TBD`.

## Health updates

A later health-only refresh may contain only `{ "health": { ... } }`. Raw HealthKit samples are not required and should not be committed to the repository.
