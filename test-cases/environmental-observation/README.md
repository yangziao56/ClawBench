# Environmental observation pilots

Two proposed public-data workflows for issue [#375](https://github.com/TIGER-AI-Lab/ClawBench/issues/375). This isolated corpus leaves released V1/V2 unchanged.

- NOAA: Boston six-minute observed water levels, September 12–13 2025, metres / MLLW / GMT. Predictions do not qualify.
- USGS: Charles River at Waltham daily mean discharge, water year 2025, cubic feet per second. Continuous data and field measurements do not qualify.

## Outcome and validation

The outcome is initiation of the correctly configured data request. Interception deliberately prevents completing that request, so it does not prove a final CSV/ZIP was saved. No claims of data analysis or downstream file delivery are made.

Both tasks passed the shared task schema, 87 offline request-contract checks, eight actual Chromium/CDP request cases and separate clean-browser website workflows in the official base runtime at commit `9dd9d442c8ec720ba4d6d4c95f2bbc0ff2a2d0df`. USGS was driven from the station page through daily discharge selection, date inputs, Mean-only download selection and Download. NOAA was driven through date controls, units/datum/timezone and Data Only. Earlier preload requests did not pass; the intended requests produced interception receipts. These were Codex-driven UI tests, not human timing studies, paid model trials or complete runner-CLI/Stage-2 judge evaluations. The full runner and request judge should be exercised during review before treating this as benchmark-ready.

The NOAA response was independently compared with 480 rows of a prior browser export; the anonymous USGS request returned 365 unique days with matching site, statistic 00003 and units. The actual USGS website uses v0 and UTC timestamp bounds; NOAA uses uppercase GMT. Query allowlists reject additional result filters and duplicate parameters. The optional USGS `api_key` field accommodates the site's own request; no key value is included in these tasks.

## Running

From a configured ClawBench checkout, use the ordinary single-task runner with a directory below this folder, or batch `--cases-dir test-cases/environmental-observation --all-cases`. Each task has a ten-minute maximum; this is a timeout, not measured human completion time. For no-model interactive review use the ordinary `--human` runner, recording the actual operator honestly.

Implementation and validation used Codex acting for Ziao Yang. Public NOAA/USGS data sources are linked in each instruction; no user conversation records or private data are included. Task scope, a possible 12-workflow expansion and individual follow-up-paper authorship remain under maintainer discussion. This two-task PR does not claim the whole-category recognition threshold has been met.
