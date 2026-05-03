# Research_Project
Data Science Research Project Part B
 
Project Area: **ANALYTICS FOR BIG BASH LEAGUE CRICKET**
 
Project Supervisor: **MIKAELA FUDOLIG**
 
---
 
## 📌 Project Overview
 
This project builds interpretable machine learning models to predict the outcome of Big Bash League (BBL) T20 cricket matches using a mid-innings snapshot at the 13th over of the second innings.
 
**Part A** establishes baseline logistic regression and decision tree models using match-state variables (runs, wickets, run rates, venue, teams).
 
**Part B** extends these baselines by engineering two novel role-based resource variables — **Remaining Batting Depth (RBD)** and **Remaining Specialist Overs (RSO)** — derived from career-level player performance across all BBL seasons (2011–2025).
 
---
 
## ⚙️ Installation & Setup
 
### 1. Prerequisites
 
Install **RStudio** for easier execution.
 
---
 
### 2. Required R Packages
 
The analysis requires the following R packages:
 
- `jsonlite`
- `dplyr`
- `purrr`
- `tidyr`
- `readr`
- `stringr`
- `ggridges`
- `forcats`
- `kableExtra`
- `caret`
- `rpart`
- `rpart.plot`
- `pROC`
- `ggplot2`
- `broom`
- `tibble`
- `DiagrammeR`
Install them in one step:
 
```r
install.packages(c(
  "jsonlite", "dplyr", "purrr", "tidyr", "readr", "stringr",
  "ggridges", "forcats", "kableExtra",
  "caret", "rpart", "rpart.plot", "pROC",
  "ggplot2", "broom", "tibble", "DiagrammeR"
))
```
 
---
 
### 3. Place Data in data/ Folder
 
Ensure the following files are inside the data folder:
 
- Dataset: https://cricsheet.org/matches/
> Download the **Big Bash League** JSON archive and extract all files into `data/bbl_json/`
 
---
 
### 4. Open the R Markdown Scripts
- For Part B — In RStudio, open `part_b.Rmd`
---
 
### 5. Knit to PDF or HTML
 
- Click the **Knit** button in RStudio to generate the analysis report.
