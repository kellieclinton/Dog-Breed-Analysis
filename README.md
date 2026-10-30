# 🐕 The Great Rescue Dog Show: AKC Popularity vs. Shelter Adoptions

## 📌 Project Overview
This project bridges the gap between commercial purebred trends and public animal welfare by comparing the American Kennel Club (AKC) popularity registers against real-world animal shelter metrics. Inspired by watching the annual AKC National Championship, this research evaluates whether public interest in elite breeds directly dictates community adoption behaviors and shelter residency durations.

The core data processing, exploratory visualizations, and statistical modeling pipelines were executed entirely in R utilizing data from the **AKC Most Popular Dog Breeds (2013-2023)**, **AKC Dog Breed Featured Descriptions**, and a historic dataset of **17,855 canine intakes from Sonoma County Animal Services**.

---

## 🧼 Data Pipeline & Feature Selection
To preserve comparability against the AKC purebred baseline, a stringent data-cleansing infrastructure was built in R:
* **Mutt & Mix Filtration:** Excluded multi-breed mixes, ambiguous records, and wild substrings (`/`, `&`, `,`) to distill down a comparable pool of **7,416 purebred records**.
* **Synonym Standardization:** Developed an intensive mapping dictionary to convert localized shelter shorthand text (e.g., `Germ Shepherd`, `Dachshund Lh`, `Schnauzer Min`) into certified AKC universal breed taxonomy names.
* **Temporal Alignment:** Structured long-form relational panels tracking breed performance across an identical overlapping window from **2013 to 2023**.

---

## 📈 Major Analytical Investigations & Statistical Modeling

### 1. Does AKC Popularity Dictate Shelter Adoptions?
**Yes.** Grouping adoptions by year and breed rank revealed an explicit operational correlation. Highly visible AKC choices directly correlate with shelter pressure; for instance, the **Chihuahua** (ranked 24th in AKC popularity) represented the absolute highest volume of local adoptions, peaking at **117 distinct adoptions per year**.

### 2. What Variables Influence Adoption Speed?
An Ordinary Least Squares (OLS) regression was fitted against the target variable **Days in Shelter** ($\text{Mean} = 46.18\text{ days}, \text{Median} = 25\text{ days}$). 

The model proved highly statistically significant ($F\text{-statistic} = 9.935, \text{df} = 46 \text{ and } 1303, p < 2.2 \times 10^{-16}$), highlighting several key predictive vectors:
* **Favorable Variables (Accelerates Adoption):** Toy, Small, or Puppy sizing tiers ($\beta_{\text{Puppy}} = -28.65, \beta_{\text{Toy}} = -31.46$), lighter weights, and higher youth friendliness metrics.
* **Unfavorable Variables (Delays Adoption):** Higher regular shedding indices ($\beta = +13.17\text{ days}$) and **Confiscated Cruelty/Neglect** intakes ($\beta = +137.14\text{ days}$).

### 3. Do Elite Top-10 Breeds Experience Faster Turnaround?
Surprisingly, tracking speed across partitioned tiers (**Top 10**, **Rank 11-50**, **Rank 51-200**) proved that less popular breeds actually clear out faster on average.

Deep-dive outlier tracking exposed that this delay is caused by legal holds: four Top-10/Tier-2 dogs (**Dachshund**, **Golden Retriever**, and **Border Collies**) were held for over **760+ consecutive days** due to complex legal field service cruelty and custody battles.

### 4. What Core Elements Drive Shelter Euthanasia?
Evaluating instances categorized under `Outcome.Type == "EUTHANIZE"` proved that behavioral constraints—rather than physical age—dictate immediate policy. While senior dogs (`Outcome.Subtype == "AGED"`) were given extended support with a mean shelter hold of **73.67 days**, severe aggression issues resulted in rapid, protective intervention with a mean hold of only **28.88 days**. Graph distributions confirmed that the vast majority of euthanized animals entered the shelter with completely *Unknown* or *Untreatable* baseline conditions.

---

## 🎯 Strategic Recommendations
* **Unified Intake Architecture:** Shelters require a centralized data portal linked directly to public AKC standards. Pre-setting universal categorical code blocks during early triage can streamline administrative processing for volunteers.
* **Targeted Allocation:** Transitioning marketing and operational budgets to sponsor health clears/vaccinations for low-demand, larger, high-shedding purebred classifications can flatten length-of-stay disparities.

---

## 💻 Tech Stack
* **Language:** R (v4.x)
* **Core Libraries:** `tidyverse`, `dplyr`, `stringr`, `plotly` (Interactive Histograms)
Now that both project files are fully documented, would you like me to show you how to write a short profile intro snippet or pinned repository overview to help frame this complete repository for potential employers?
