# 🏥 Medical Insurance Cost Predictor

Predicting healthcare insurance charges from policyholder personal attributes using regression analysis.

---

## 📋 Project Overview

As healthcare costs continue rising, the ability to predict what a policyholder might incur in medical charges is valuable — both for insurance companies setting premiums and for individuals estimating their costs.

This project analyzes a synthetic US census-based insurance dataset to:
- Identify which personal attributes correlate most strongly with medical charges
- Build predictive regression models for healthcare costs

**Key Finding:** Smoking status, age, and BMI are the strongest predictors of insurance charges — smoking alone carries a coefficient of +$23,743 in our OLS model.

---

## 📊 Dataset

| Variable | Description | Type | Range |
|---|---|---|---|
| `age` | Policyholder age | int | 18–64 |
| `sex` | Gender | categorical | male / female |
| `bmi` | Body Mass Index | float | 15.96–53.13 kg/m² |
| `children` | Number of dependents | int | 0–5 |
| `smoker` | Smoking status | categorical | yes / no |
| `region` | US geographic region | categorical | NE, NW, SE, SW |
| `charges` ⭐ | Medical costs billed | float | $1,121–$63,770 |

**Source:** [Kaggle — Healthcare Insurance Dataset](https://www.kaggle.com/datasets/willianoliveiragibin/healthcare-insurance/data)  
**Size:** 1,338 rows, 7 variables (1 duplicate removed)

---

## 🛠️ Methods & Tools

**Libraries used:**
- `pandas`, `numpy` — data manipulation
- `matplotlib`, `seaborn` — visualization
- `scipy`, `statsmodels` — statistical analysis
- `sklearn` — machine learning models

**Models applied:**
- Ordinary Least Squares (OLS) Linear Regression
- Decision Tree Regression

**Preprocessing steps:**
- Duplicate removal via `drop_duplicates()`
- BMI outlier removal using IQR method (9 entries removed, BMI ≥ 47)
- One-hot encoding for categorical variables (`region`, `sex`, `smoker`)
- Feature engineering: `bmi_group` and `age_group` derived variables

---

## 📈 Results

### Exploratory Data Analysis
- **Smoking** shows the strongest visual separation in charges across all plots
- **Age** shows a clear positive trend with charges
- **BMI**, especially in the obese range (≥30), correlates with higher costs
- **Sex**, **region**, and **number of children** showed weak or no meaningful correlation

### Correlation Heatmap
| Feature | Pearson r² with Charges |
|---|---|
| `smoker_encoded` | **0.79** |
| `age` | 0.30 |
| `bmi` | 0.20 |
| `sex`, `children`, `region` | ~0.00 |

### Model Performance
| Model | R² Score | Notes |
|---|---|---|
| OLS Linear Regression | **0.749** | Features: age, BMI, smoker |
| Decision Tree Regression | **0.752** | Feature importance: smoking > age > BMI |

---

## 🔍 Key Insights

- **Smokers pay dramatically more** — regardless of BMI, age, sex, or region
- **Obese smokers** incur the highest charges of any subgroup
- **Southeast smokers** tend to have higher costs than northern smokers
- Age is a significant predictor, but smoking overrides it across all age groups
- Sex, region, and number of children are **not reliable predictors** of insurance costs

---

## 📁 Repository Structure

```text
├── Group_Code_Final.ipynb   # Full analysis notebook
├── Group_4-Report.docx      # Detailed project report
├── Summary_Paper.docx       # Summary write-up
├── insurance.csv            # Dataset (Kaggle source)
└── README.md
```

---

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/IgaMeddie/healthcare-analysis/tree/main
cd medical-insurance-cost-predictor

# Install dependencies
pip install pandas numpy matplotlib seaborn scipy scikit-learn statsmodels

# Launch the notebook
jupyter notebook Group_Code_Final.ipynb
```

---

## 📚 References

1. [Healthcare Insurance Dataset — Kaggle](https://doi.org/10.34740/KAGGLE/DSV/6678394)
2. [US Census Bureau — Population by Sex](https://www.census.gov/quickfacts/fact/table/US/LFE046222)
3. [CDC — Cigarette Smoking in the US](https://www.cdc.gov/tobacco/campaign/tips/resources/data/cigarette-smoking-in-united-states.html)
4. [OLS Regression — XLSTAT](https://www.xlstat.com/en/solutions/features/ordinary-least-squares-regression-ols)
5. [Decision Tree Algorithm — Analytics Vidhya](https://www.analyticsvidhya.com/blog/2021/08/decision-tree-algorithm/)