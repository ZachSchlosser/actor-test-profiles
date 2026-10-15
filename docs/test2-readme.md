# Test 2 — Rule Cards

Nine rule-card profiles for the persona-comparison experiment, built from the dated rows and context events in `data/`, following the site's own protocols (P1 dated triggers, P2 computed gaps, P3 at least three independent episodes — same-cause triggers within 30 days count as one wave). Existing persona rules are carried and extended; the five actors whose personas held only hypotheses now have generated cards. Each card carries delay (median/range/n), size where the data quantifies it, direction, leave-one-out verb stability, and per-episode sources.

**NVIDIA** (company, cutoff 2026-07-01) — Best rule: N1, when the US imposes an export restriction that hits its China chips it files an 8-K within 0–6 days (median 5), the filing itself usually breaking the news; N2 and N3 are same-day statement rules for US policy moves and Beijing pressure. Background research: China (incl. Hong Kong) was ~13% of FY2025 revenue ($17.1bn of $130.5bn), via Bullfincher's compilation of NVIDIA 10-K geographic disclosures (bullfincher.io).

**Cyberspace Administration of China** (government, cutoff 2025-01-01) — Best rule: C1, a published draft is followed by a signed, co-issued final text (31 episodes, median 189 days), with the C2a/C2b/C3 pipeline (office meeting → signing → entry into force → first filing list) making CAC's whole rule lifecycle forecastable on timing. Research note: CAC's one completed foreign-chip-firm review (Micron, 2023) ended in a purchase ban, cited from the A098 row source (cac.gov.cn).

**Ministry of Commerce (MOFCOM)** (government, cutoff 2026-01-01) — Best rule: M2, a large US or allied chip escalation draws a critical-mineral export control within 1–10 days (median 3), alongside M1's near-certain same-day condemnation. Research note: the October 2025 rare-earth rule reaches items with ≥0.1% Chinese rare-earth content, cited from the MC25 announcement (mofcom.gov.cn).

**Baidu** (company, cutoff 2026-01-01) — Best rule: BD3, when a US rule or Chinese purchase halt cuts NVIDIA supply, Baidu plays down the hit at its next scheduled event (median 35 days), citing stockpiles and its 30,000-chip Kunlun P800 cluster (BD14). BD1 (matching rivals' open models and price cuts) is a 2-wave signal; all sources are row sources.

**DeepSeek** (company, cutoff 2026-01-01) — Best rule: DS1, a foreign app ban or inquiry draws the minimum same-day answer — pull the app, agree a suspension, or stay silent (Italy, Korea, Berlin). DS2 is the strategic one: after NVIDIA access is cut, its next flagship ships open-weight with day-zero Chinese-chip support (21–106 days). No outside research needed; all sources are row sources.

**Huawei** (company, cutoff 2026-01-01) — Best rule: HU5 (generated), a public allegation of sanctions violations or model copying draws a next-day denial or no comment, three independent waves at exactly 1 day. HU1–HU3 cover the self-reliance and Ascend answers to US tightening and NVIDIA's China swings. Background research: Huawei's Entity List addition effective 16 May 2019, via the Federal Register final rule at govinfo.gov.

**Jensen Huang** (individual, cutoff 2026-07-01) — Best rule: R2, when a US restriction or Chinese purchase block cuts NVIDIA's China sales he calls the policy a mistake in public within 2–5 weeks, framing it as handing the market to Huawei. R1 (Beijing trip after a restriction), R4 (reframing safety alarms), R3 (same-day walk-back of off-message remarks) and R5 (accepts Trump invitations) complete the card; all sources are row sources.

**Ministry of Industry and Information Technology (MIIT)** (government, cutoff 2026-01-01) — Best rule: MI3, when CAC signs an AI rule that MIIT co-issues, MIIT co-issues within days (0–16 days across three rules; two build episodes before the cutoff). MI1 (steering buyers after US easing), MI2 (quiet state-network chip substitution) and MI4 (promoting a breakout open model) round it out; sources are row sources plus CAC signing rows.

**State Administration for Market Regulation (SAMR)** (government, cutoff 2026-01-01) — Best rule: S1, US chip escalation draws an antitrust probe of a US chip firm within 3–11 days (NVIDIA twice, Qualcomm once; two independent waves). S4 (tariffs → probe of a US firm), S2 (talks/truces → suspend or drop probes, never a formal closure) and S3 (same-day co-issuing of CAC AI rules) complete the card; all sources are row sources.

## Verification

All nine files parse as JSON. Every episode trigger and response id resolves to a row or context event in the data (CAC office-meeting, holiday and effective-date anchors are labelled `OFFICE-`/`LNY-`/`EFFECT-` with dates documented in the CAC persona). Every source URL is either a row/context source or one of the two fetched research URLs. Gaps were computed from row dates (effective-date and month-precision overrides noted in the build). Rule counts by status:

| actor | rule | signal | anecdote | episodes |
|---|---|---|---|---|
| nvidia | 3 | 2 | 0 | 16 |
| cac | 5 | 1 | 0 | 84 |
| mofcom | 2 | 2 | 0 | 18 |
| baidu | 1 | 1 | 2 | 8 |
| deepseek | 0 | 2 | 1 | 6 |
| huawei | 1 | 3 | 0 | 10 |
| jensen-huang | 0 | 3 | 2 | 9 |
| miit | 0 | 2 | 2 | 7 |
| samr | 0 | 3 | 1 | 9 |

---

**Correction (post fact-check):** 41 of the original 167 episodes used response rows dated after their actor's cutoff — i.e., drawn from the hidden answer key. All rule statistics on the site have been recomputed from pre-cutoff episodes only; excluded episodes are retained per rule under `post_cutoff_episodes`. Two rules (R4 Jensen Huang, S3 SAMR) were built entirely from post-cutoff rows and are excluded from the exam. Episode totals in the original verification table above describe the pre-correction build.
