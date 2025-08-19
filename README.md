# Match 3D – Shop Icon A/B Test Analysis

##  Overview  
In this project, I evaluated whether a redesigned **Shop** icon would boost shop entry rates for new users of *Match 3D* by at least **10%**. The Product team proposed a **20% / 80%** (Test / Control) split, but the dataset actually reflects a roughly **50/50** split. I analyzed both scenarios for completeness and robustness.

##  Quick Summary  
- **Result:** The new icon **did not increase** shop entrances in a meaningful way and significantly **reduced** downstream KPIs.  
  - **Purchase rate:** Control 13.4% → Test 8.7% (p ≪ 0.001)  
  - **ARPU:** \$1.77 → \$1.05 (p ≪ 0.001)  
  - **Engagement:** Sessions, playtime, levels, and rewarded videos all declined significantly in Test.  
- **Segments:** Negative impact is consistent across **Android/iOS** and **US/Non-US** users.  
- **20/80 robustness test:** Same pattern holds even when subsampling to match the Product team’s suggested 20/80 allocation.

**Recommendation:** *Do not roll out the new Shop icon.* Instead, conduct usability research and consider iterative UI improvements with retention safeguards in place.

---

##  Repository Structure

.
├── post_experiment_analysis.ipynb # Fully documented notebook with visuals, stats, and stories.

├── lionstudios_data_analyst_take_home.csv # Session-level dataset (tracked via Git LFS if large).

├── README.md

├── requirements.txt # Required Python environment (pandas, numpy, scipy, etc.).

├── .gitignore # Ignored files (e.g., caches, checkpoints).

└── .gitattributes # Git LFS tracking for large files.



---

##  Setup & Reproducibility

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook post_experiment_analysis.ipynb
