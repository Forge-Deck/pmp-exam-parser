# PMI Exam Analysis Parser

A small browser-only page for turning PMI CCRS Exam Analysis source code into a readable raw-score breakdown.

## What it does

- Reads pasted full HTML/source, body-only HTML, Kendo chart snippets, or raw JSON arrays/objects.
- Pulls out `ScorePercentage`, `TotalQuestions`, domains, task names, domain weights, and visible page result metadata where available.
- Estimates raw scores using `round(TotalQuestions × ScorePercentage / 100)`.
- Checks summed task totals against the embedded domain totals.
- Includes all rows where `TotalQuestions > 0`, even if the PMI display marks the row as blank/no-question.
- Flags rows where the PMI display indicator appears inconsistent with the embedded question count.
- Adds an unofficial band estimate for rough AT/T/BT/NI comparison.
- Creates a readable Reddit/comment share summary with a consistent `PMP_DATA` line for later community modelling.
- Hides the input and instructions after parsing so the result is shown first.
- Ignores PMI ID, account names, links, analytics, and other personal page data.
- Runs locally in the browser. No server or API is used.

## Hosting on GitHub Pages

1. Create a GitHub repository.
2. Upload `index.html` to the repository root.
3. Open **Settings → Pages**.
4. Set source to **Deploy from a branch**.
5. Select the `main` branch and `/root`.
6. Save.

## Share summary format

The copy button outputs a Reddit-friendly markdown summary with:

- headline raw estimate;
- domain breakdown table;
- low / medium task table;
- unofficial band read;
- one compact `PMP_DATA` line for later aggregation.

The goal is for people to be able to read it normally in a comment while still keeping the numbers consistent enough to collect and model later.

## Attribution

This tool was built from a community method shared on Reddit. Credit to the original poster, [u/AvatarPurusha](https://www.reddit.com/user/AvatarPurusha/), for documenting the current Exam Analysis source-code approach.

Original Reddit post: https://www.reddit.com/r/pmp/s/1T1hCmyN6U

## Notes

The pasted content must contain the embedded chart data with `ScorePercentage`, `TotalQuestions`, and `Tasks`. The full page is not required if the relevant data block is present.

The raw score and band estimate are not official PMI results. The band estimate is based on limited community datapoints from older/pre-update reports and is not validated against PMBOK8-oriented exam results. PMI may change the page structure or scoring model at any time.

## PM Cram
The ultimate PMP study companion.  https://forge-deck.github.io/pmcram/
