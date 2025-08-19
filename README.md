Match 3D – Shop Icon A/B Test (Take-Home)

Goal. Evaluate whether a redesigned Shop icon increases shop entrances by ≥10% for new users. Product initially proposed a 20/80 (Test/Control) split; the provided dataset is ~50/50, so I report results for both and check robustness.

Deliverables.

Notebook: post_experiment_analysis.ipynb (full analysis, visuals, stats)

This README: executive summary, how to run, and methods

TL;DR (Executive summary)

Result: The new icon did not improve shop entrances in a meaningful, durable way and significantly worsened downstream KPIs.

Purchase rate: Control 13.4% vs Test 8.7% (50/50 split; p ≪ 0.001).

ARPU: $1.77 (Control) vs $1.05 (Test); p ≪ 0.001.

Engagement (sessions, playtime, levels, RVs): all significantly lower in Test.

Segments: Negative on both Android/iOS and US/Non-US (not driven by one cohort).

20/80 robustness: Subsampled to ~20/80 (as per brief) → same direction & story, slightly larger p-values (expected with less power).

Recommendation: Do not roll out the new icon as-is. Prefer small, iterative redesign + qualitative UX checks, then re-test.

.
├─ post_experiment_analysis.ipynb   # End-to-end analysis: data prep, KPIs, stats, visuals
├─ lionstudios_data_analyst_take_home.csv  # Provided session-level dataset (LFS if large)
├─ README.md
├─ requirements.txt                 # Minimal env to run the notebook
└─ .gitignore / .gitattributes      # LFS tracking if needed


# 1) Create & activate a clean environment (Python 3.10+)
python3 -m venv .venv
source .venv/bin/activate

# 2) Install required packages
pip install -r requirements.txt

# 3) Open the notebook
jupyter notebook post_experiment_analysis.ipynb
# or open in VS Code and run all cells

Data & KPIs (what I measured)

Each row = a user session (multiple rows per user). I compute user-level KPIs:

Shop open (icon): whether a user opened the shop via the icon at least once

Purchase rate: whether a user made any IAP

ARPU: total revenue per user

Engagement: sessions, total playtime (minutes), levels played, rewarded videos watched

Segments: platform (android/ios) and country (US/Non-US)

The primary product KPI is “increase in shop entrances”, evaluated first-day and overall. Secondary KPIs (conversion, ARPU, engagement) ensure we don’t trade clicks for churn.


Methods (statistics & design choices)

Binary rates (purchase rate, shop-icon open rate): Two-proportion z-tests (large-N, independent users).

Skewed continuous metrics (ARPU, playtime): Welch’s t-tests (unequal variances/sizes); I also sanity-checked revenue with non-parametric tests where appropriate.

Why these tests? They’re standard, interpretable, robust for A/B at this scale. 
Wikipedia
+1
sites.nicholas.duke.edu

Allocation. Brief says 20/80; data is ~50/50. I:

Analyze the dataset “as is” (~50/50),

Recreate 20/80 via stratified subsampling (platform×country) to match the brief, and confirm the same conclusions hold.

Results (concise)
1) Main (50/50)

Purchase rate: 13.4% → 8.7% (Test), p ~ 1e-26

ARPU: $1.77 → $1.05, p ~ 1e-26

Shop opens (overall): 1.13 → 0.76 per user, p ~ 1e-62

Icon opens (per user): 0.434 → 0.410, ns (p ~ 0.09)

Engagement: sessions, playtime, levels, RVs all down in Test (p ≪ 0.001)

Interpretation. The new icon delivered a small day-0 curiosity bump but users churned earlier and monetized less. Net effect: negative.

2) Segments

Android and iOS: both negative; iOS impact is larger (purchase & ARPU drop).

US and Non-US: both negative; consistent pattern across geos.

3) Sensitivity (20/80, as per brief)

Same direction & practical size: Control > Test on revenue and engagement; icon-open rate remains ns.

Lower power → p-values larger, but conclusions unchanged.

Recommendations

Do not roll out the new icon as-is.

Run a UX/qual loop (click-path videos, quick surveys) to learn why it deters players (e.g., salience vs. confusion vs. “too salesy”).

Iterative A/B: Try subtle design tweaks (size, color, timing of first appearance post-tutorial), with retention guardrails.

Consider contextual prompts (well-timed interstitial after need-creating moments) rather than persistent visual pressure.

If still pursuing visibility, test segment-specific rollout (e.g., later-stage users) where icon salience is less likely to harm onboarding.

Reproducibility & code style

Notebook cells are linear, commented, and parameterized where helpful.

I compute KPIs at user-level to avoid session-count bias.

Segmentation & 20/80 checks are encapsulated in reusable blocks.

For real-world deployment, I’d:

Extract helpers into small functions/modules,

Add simple unit checks (schema, NA rates, basic invariants),

Persist clean intermediate tables for review.
