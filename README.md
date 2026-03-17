# Manager Effectiveness Analysis

**HR Analytics Portfolio — Project 2**  
[Tobi Abanishe](https://github.com/TobiAbanishe) · [Project 1: Employee Attrition Model](https://github.com/TobiAbanishe/attrition-model)

---

## What This Project Does

This project applies the **Google Project Oxygen** framework to measure and improve manager effectiveness using employee survey data. It produces four outputs useful to any HR or People Analytics team:

1. **Survey Response Analysis** — how employees rate their managers across the 8 Oxygen behaviors
2. **Manager Effectiveness Score** — a single composite metric per manager, normalised to a 0 to 100 scale
3. **Team Outcome Correlations** — quantified relationships between manager quality and team attrition, engagement, and performance
4. **Manager Clustering** — K-Means grouping of managers into three actionable tiers: High Effectiveness, Developing, and Needs Support

---

## Background: Google Project Oxygen

In 2008, Google launched an internal research initiative to find out whether managers actually matter and what separates good ones from bad ones. Analysing thousands of performance reviews, upward feedback surveys, and manager interviews, their researchers identified 8 key behaviors shared by the most effective managers in the company:

| # | Behavior |
|---|----------|
| 1 | Is a good coach |
| 2 | Empowers the team and does not micromanage |
| 3 | Creates an inclusive environment, showing concern for success and wellbeing |
| 4 | Is productive and results oriented |
| 5 | Is a good communicator — listens and shares information |
| 6 | Supports career development and discusses performance |
| 7 | Has a clear vision and strategy for the team |
| 8 | Has key technical skills to help advise the team |

This project operationalises those 8 behaviors into a measurable scoring system using simulated survey data.

---

## Repo Structure

```
manager-effectiveness-analysis/
│
├── data/
│   ├── generate_data.py        # Synthetic dataset generator
│   ├── managers.csv            # Manager reference table (60 managers)
│   ├── survey_responses.csv    # Individual employee survey ratings
│   └── team_outcomes.csv       # Team-level attrition, engagement, performance
│
├── notebooks/
│   └── manager_effectiveness.ipynb   # Full analysis notebook
│
├── sql/
│   └── manager_metrics.sql     # 6 reusable SQL queries for reporting
│
├── outputs/                    # Charts saved during notebook execution
│
├── requirements.txt
└── .gitignore
```

---

## How to Run

### 1. Clone the repo

```bash
git clone https://github.com/TobiAbanishe/manager-effectiveness-analysis.git
cd manager-effectiveness-analysis
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Generate the synthetic dataset

```bash
python data/generate_data.py
```

This creates three CSV files in the `data/` folder.

### 4. Open the notebook

```bash
jupyter notebook notebooks/manager_effectiveness.ipynb
```

Run all cells in order. Charts are automatically saved to the `outputs/` folder.

---

## Key Findings

### Manager effectiveness is strongly correlated with team outcomes

Higher effectiveness scores are associated with meaningfully lower attrition, higher engagement, and higher team performance — consistent with the original Project Oxygen findings at Google.

### Three distinct manager profiles emerge from clustering

| Tier | Description | Recommended Action |
|------|-------------|-------------------|
| High Effectiveness | Strong ratings across most or all behaviors | Recognise and use as internal mentors |
| Developing | Solid in some areas, weaker in others | Targeted coaching based on individual behavior gaps |
| Needs Support | Consistently low across all behaviors | Immediate development programme, leadership review |

### Behavior gaps vary by department

Some departments show consistently stronger management than others. The department-level heatmap in the notebook surfaces where organisation-wide coaching investment would have the most impact.

---

## SQL Queries

The `sql/manager_metrics.sql` file contains 6 ready-to-run queries:

| Query | Purpose |
|-------|---------|
| 1 | Average behavior scores per manager |
| 2 | Composite effectiveness score (normalised 0 to 100) |
| 3 | Effectiveness score joined with team outcomes |
| 4 | Department-level summary |
| 5 | Top and bottom 10 managers leaderboard |
| 6 | Weakest behavior per manager (for coaching plans) |

These are written in standard SQL and work in PostgreSQL, SQLite, or any ANSI-compatible database.

---

## Tools and Libraries

| Tool | Purpose |
|------|---------|
| Python 3.10 | Core language |
| pandas | Data manipulation |
| numpy | Numerical computation |
| scikit-learn | K-Means clustering, StandardScaler |
| matplotlib / seaborn | Visualisation |
| scipy | Pearson correlation |
| SQL | Aggregation and reporting queries |

---

## Data Note

All data in this project is **synthetically generated** using `data/generate_data.py`. The dataset is designed to reflect realistic HR patterns — manager ratings follow a beta distribution, and team outcomes are correlated with a latent effectiveness score — but it contains no real individuals or organisations.

---

## Portfolio

This is Project 2 in my HR Analytics portfolio.

- **Project 1 — Employee Attrition Model:** Predicts which employees are at risk of leaving using logistic regression and random forest. → [github.com/TobiAbanishe/attrition-model](https://github.com/TobiAbanishe/attrition-model)
- **Project 2 — Manager Effectiveness Analysis:** This project.

---

*Built by [Tobi Abanishe](https://github.com/TobiAbanishe)*
