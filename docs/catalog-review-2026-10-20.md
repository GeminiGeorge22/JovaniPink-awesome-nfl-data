# Catalog review - October 20, 2026

This is an automated transport audit plus targeted public-source content review. It is
not a catalog-wide human review, dataset-quality qualification, or license grant. Existing
catalog-wide review dates and schema 1.1 uncertainty defaults remain unchanged.

## Review basis

- Baseline: `9615b4f939ab51691e3c1dc8f5cec2ffd2f38da8`.
- Original contributor commits preserved with `git cherry-pick -x`:
  - [PR #16](https://github.com/JovaniPink/awesome-nfl-data/pull/16), @noahowsh,
    `33952bd3471fba07a8fde129ce8f8ba670b56361` (EndzoneAPI).
  - [PR #17](https://github.com/JovaniPink/awesome-nfl-data/pull/17), @noahowsh,
    `fae2d49358de9d58c6631ce6d59ab8b4e0f10072` (NoPunt access clarification).
- Both contributors' exact heads passed unit, README, and projection checks in temporary
  snapshots; neither PR exposed hosted checks during this review.

## Targeted findings

| Source | October 20 evidence | Change and limitation |
| --- | --- | --- |
| [nflverse schedule](https://nflreadr.nflverse.com/articles/nflverse_data_schedule.html) and [injury release](https://github.com/nflverse/nflverse-data/releases/tag/injuries) | Publisher documents daily in-season injury updates; 2025 and 2026 release assets exist. The inspected 2026 CSV had 1,789 rows for weeks 1-6, with the asset updated October 20. | Removed the obsolete post-2024 gap. File existence does not prove full current-week coverage. Participation remains postseason-only from 2023 onward. |
| [EndzoneAPI documentation](https://endzoneapi.com/docs) and [terms](https://endzoneapi.com/terms) | Publisher describes HTTP/MCP access, API keys, credits, standalone redistribution restrictions, raw-odds restrictions, and an exception preserving separately open-licensed data. | Replaced the PR's overly narrow competing-service restriction. No authenticated data-quality or coverage qualification was performed. |
| [NoPunt documentation](https://www.nopunt.com/docs) | `api/picks.json`, `api/teams.json`, and `api/power-rankings.json` returned JSON without authentication. The picks response identified season 2026, week 7. | Retained the contributor access clarification, model labels, subscription distinction, and unverified-performance caveat. |

The initial 61-entry scan found four HTTP 403 responses and no confirmed missing URL.
Subsequent observations can differ by method, user agent, and time. Retain the blocked
reference sites; do not reinterpret access controls as discontinued resources.

[License issue #1](https://github.com/JovaniPink/awesome-nfl-data/issues/1) remains open.
[Renovate #15](https://github.com/JovaniPink/awesome-nfl-data/pull/15) remains separate;
its existing hosted Python 3.11/3.14 checks passed at review time.

## Validation and boundaries

Run the canonical commands from the repository root:

```sh
python3 -m unittest discover -s tests -v
python3 scripts/validate_readme.py README.md
python3 scripts/build_resource_index.py --check
python3 scripts/audit_links.py --output /tmp/catalog-link-audit.json
```

The offline suite includes controlled-response tests for redirects to unrelated HTTP 200
pages, HEAD rejection and false 404 responses, blocked requests, rate limits, missing
responses, transient errors, redirect loops, bounded GET bodies, and catalog preservation.
The live audit is deliberately outside CI. Its JSON records each request and observation;
HTTP success alone does not verify content, freshness, rights, or current data coverage.

Existing resource identifiers and creation dates were compared with the baseline. All
surviving identities retain their dates. Replacement URLs get new identities with explicit
October 20 inclusion dates; older URL dates remain in configuration as historical metadata.
Contributor-supplied identity dates remain attached to their original commits.

Original contributor PRs, Renovate onboarding, and open issues are unchanged. No merge,
contributor feedback, license change, paid API access, or dataset import is part of this
integration. Source descriptions based on public documentation do not establish
independently tested authenticated behavior. Hosted CI on these local integration commits
has not run.

## Final integration check

- Offline unit suite: 40 tests passed; README validation, generated-index check, and whitespace check passed.
- Final automated scan: 62 entries; blocked/authentication-required: 7, reachable: 54, redirected: 1.
- Observation interval: `2026-10-20T19:31:24+00:00` through `2026-10-20T19:31:30+00:00`.
- [Full link-audit JSON](link-audits/2026-10-20.json) includes the matching catalog SHA-256 and per-request evidence.
- Redirects and blocks remain review observations, not proof of content relevance or dead links.
