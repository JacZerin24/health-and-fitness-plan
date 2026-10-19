# ShiftFit private import format

The public `data.json` contains only a generic training template and no private measurements. The dashboard reads personal data from browser storage and merges private JSON refreshes into it.

## Example: health-only refresh

```json
{
  "version": 2,
  "health": {
    "snapshotDate": "2030-01-05",
    "latestSleepHours": 7.8,
    "sleep7d": 7.5,
    "sleep30d": 7.4,
    "steps7d": 7200,
    "steps30d": 6900,
    "rhr7d": 65,
    "hrv7d": 40,
    "series": {
      "steps": [{"date": "2030-01-04", "value": 7100}],
      "sleep": [{"date": "2030-01-04", "value": 7.6}]
    }
  },
  "meta": { "lastPrivateUpdate": "2030-01-05T12:00:00-06:00" }
}
```

## Optional fields

- `profile`: `startWeight`, `targetWeight`, `heightIn`, `protein`, `commuteMin`.
- `plan.phases`: date-bounded plan phases with `start`, `end`, `cal`, `protein`, `steps`, `strength`, `cardio`.
- `plan.nutrition`: display text for protein/fat/fiber/hydration ranges.
- `scheduleRanges`: `{start,end,code}` inclusive; `scheduleOverrides`: a map of date to shift code.
- `weightEntries`: manually entered `{date,weight,waist}` array.
- `health.series`: daily `{date,value}` arrays keyed by `steps`, `active`, `rhr`, `hrv`, `sleep`, `bodyMass`, `vo2max`.
- `meta`: optional `scheduleStart`, `scheduleThrough`, and `lastPrivateUpdate`.

Valid shifts: `G` 6a–2p, `I` 8a–4p, `X` supernumerary, `K` 10a–6p, `M` 12p–8p, `P` 2p–10p, `R` 4p–midnight, `W` 10p–6a, `A` midnight–8a, `OFF`, and `TBD`.

Imports merge nested objects, including new health metrics and shift overrides. Arrays (for example `plan.phases`, `health.series.steps`) replace the previous array when supplied. Omitted sections remain unchanged. Export a full backup when you want to transfer all local data to another device.

**Safety:** GitHub Pages cannot directly use Apple HealthKit or a private Google Calendar without a separately authorized backend. Never put this private JSON or credentials into the GitHub repository.
