BBL Cricket Win Prediction — Data Science Research Project
University of Adelaide — Master of Data Science
Course: Data Science Research Project (Part A & Part B)
Project Area: Analytics for Big Bash League Cricket
Supervisor: Mikaela Fudolig

Overview
This project builds interpretable machine learning models to predict the outcome of Big Bash League (BBL) T20 cricket matches using a mid-innings snapshot taken at the end of the 13th over of the second innings.
Part A establishes baseline logistic regression and decision tree models using match-state variables (runs, wickets, run rates, venue, teams).
Part B extends these baselines by engineering two novel role-based resource variables — Remaining Batting Depth (RBD) and Remaining Specialist Overs (RSO) — derived from career-level player performance across all BBL seasons (2011–2025).
Key Results
ModelAccuracyAUCPart A — Logistic Regression84.6%0.884Part A — Decision Tree76.9%0.834Part B — Logistic Regression (tuned)87.6%0.913Part B — Decision Tree (tuned)89.4%0.910

Repository Structure
├── Part_A.Rmd              # Part A: Baseline models (R Markdown)
├── prep_final.Rmd          # Part B: Extended models with RBD & RSO (R Markdown)
├── data/
│   └── bbl_json/           # BBL match JSON files from Cricsheet (not included)
└── README.md

Note: Raw data files are not included in this repository. See the Data section below for download instructions.


Data
All match data is sourced from Cricsheet — a free, open archive of ball-by-ball BBL match data in JSON format.

Go to https://cricsheet.org/matches/
Download the Big Bash League JSON archive
Extract the JSON files into data/bbl_json/

The dataset used in this project covers 618 matches across BBL seasons 2011–2025, comprising 143,323 deliveries across 8 teams and 22 venues.

Installation & Setup
Prerequisites

R (version 4.0 or higher recommended)
RStudio for easier execution

Required R Packages
Part A packages:
rinstall.packages(c(
  "jsonlite", "dplyr", "purrr", "tidyr", "readr", "stringr",
  "ggridges", "forcats", "kableExtra",
  "caret", "rpart", "rpart.plot", "pROC",
  "ggplot2", "broom", "tibble"
))
Part B packages (all of the above, plus):
rinstall.packages(c("scales", "gridExtra"))

How to Run
Part A — Baseline Models

Open Part_A.Rmd in RStudio
Ensure the BBL JSON files are placed in data/bbl_json/
Click Knit to generate the full analysis report (PDF or HTML)

The script will:

Parse all BBL JSON match files into a delivery-level data frame
Standardise venue names and assign home teams
Extract 13-over second-innings snapshots
Train and evaluate logistic regression and decision tree models
Generate ROC curves, confusion matrices, and variable importance plots
Produce player role classifications (Batter / Bowler / Allrounder)

Part B — Extended Models (RBD & RSO)

Open prep_final.Rmd in RStudio
Ensure the BBL JSON files are placed in data/bbl_json/
Click Knit to generate the extended analysis report

Additional steps in Part B:

Computes career-level player weightage scores (W_batter, W_bowler)
Constructs RBD (Remaining Batting Depth) and RSO (Remaining Specialist Overs) at the 13-over snapshot
Engineers pressure features: pressure ratio, runs per ball, wicket rate, RBD × pressure interaction
Trains and evaluates Part B models against Part A baselines
Performs threshold tuning using Youden's J statistic
Runs a Leave-One-Out (LOO) leakage analysis on player weightage scores


Methodology Summary
Snapshot Construction
A predictive snapshot is extracted at the first delivery after the 13th over of the second innings, capturing: current runs, wickets lost, balls remaining, current run rate, required run rate, home team, venue, batting team, bowling team, and first-innings target.
Player Role Classification
Players are classified using career workload thresholds across all BBL data:

Batter: ≥ 20 career deliveries faced
Bowler: ≥ 18 career deliveries bowled
Allrounder: meets both thresholds (takes precedence)

Resource Variables

RBD — quality-weighted sum of batter weightage scores for undismissed batters at the 13-over mark. Pearson correlation with match outcome: r = 0.512
RSO — quality-weighted sum of remaining specialist overs for qualified bowlers (W_bowler > 0.3). Pearson correlation with match outcome: r = −0.090

Models
Both logistic regression and decision tree models are trained on an 80/20 stratified train-test split (seed = 42), evaluated at both a default threshold (0.5) and a Youden-optimal threshold derived from the ROC curve.

Dependencies
PackagePurposejsonliteParsing BBL JSON match filesdplyr, purrr, tidyrData wranglingstringrString manipulation / venue standardisationggplot2, ggridgesVisualisationcaretTrain/test splitting, confusion matrixrpart, rpart.plotDecision tree modellingpROCROC curves and AUC calculationbroom, tibbleModel output tidyingkableExtra, forcatsTable formatting and factor handling

Citation
If you use this work, please cite:

Korde, B.M. (2026). Analytics for Big Bash League Cricket — Mid-innings Win Probability Prediction using Role-Based Resource Variables. Data Science Research Project, School of Mathematical Sciences, University of Adelaide.

Data sourced from: Cricsheet (2009). Big Bash League. https://cricsheet.org/matches/

License
This project was submitted for academic assessment at the University of Adelaide. Code is made available for educational and research purposes.
