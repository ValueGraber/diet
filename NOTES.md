## Diet page (`/diet/`)
- Separate weight-loss planner at https://valuegraber.github.io/diet/. Source `src/diet.html` (same body as Mon's Claude artifact), build with `python3 tools/build_diet.py` → `index.html`. Not part of `tools/build.py`.
- Storage: localStorage `wl-profile`, `wl-day-YYYY-MM-DD`, `wl-week-<monday>`; signed in → Firestore `diet/{uid}` (profile), `diet/{uid}/days/{date}`, `diet/{uid}/weeks/{monday}`. Same Firebase project/auth as ValueGrab. First sign-in uploads local data if the account has no profile yet.
- Features: exercise demos (`EX` steps + `POSES` stick figures, `openEx`), lift log (`profile.lifts`, `logLift`, `hintFor`), rest `Timer`, `profile.recent` foods + `copyMeal`, 7-day `renderSummary` + CSV `exportCsv`, waist/hip in `profile.weights`.
- Needs rule: `match /diet/{uid}/{rest=**} { allow read, write: if request.auth != null && request.auth.uid == uid; }`

- 2026-11-26: moved out of valuegraber.github.io into its own repo ValueGraber/diet (same URL /diet/).
