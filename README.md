# King County Housing Price Prediction with Multiple Regression

## 🎯 Project Overview

Built and evaluated multiple regression models to predict housing prices in King County, Washington using a dataset of 2,692 recent home sales. Developed first-order and complete second-order regression models, achieving **R² = 0.81** with advanced feature engineering including quadratic terms and interaction effects.

## 📊 Key Results

| Model | R² | Adjusted R² | F-Statistic | Key Features |
|-------|-----|-------------|-------------|--------------|
| **First-Order Model** | 0.603 | 0.602 | 679.3 (p < 2.2e-16) | Living area, age, bathrooms, view |
| **Second-Order Model** | **0.809** | **0.808** | 2272 (p < 2.2e-16) | School rating, crime rate, quadratic terms, interaction |
| **First-Order with Interaction** | 0.800 | 0.799 | 3573 (p < 2.2e-16) | School rating, crime, interaction only |

## 🛠️ Technologies & Methods

**Programming & Tools:**
- R programming language
- Statistical modeling packages
- Data visualization

**Statistical Techniques:**
- Multiple linear regression (first-order and second-order)
- Correlation analysis with Pearson coefficients
- Nested models F-test for model comparison
- Feature engineering (quadratic terms, interaction effects)
- Model diagnostics (residual plots, Q-Q plots)

**Statistical Methods:**
- Overall F-tests for model significance
- Individual t-tests for coefficient significance (α = 0.05)
- Confidence intervals for mean predictions (90%)
- Prediction intervals for individual forecasts (90%)
- R² and adjusted R² for model fit assessment

## 🔬 Models Developed

### Model 1: First-Order Multiple Regression ⭐
**Predictors:** Living area sqft, upper-level sqft, home age, bathrooms, view category (road/trees/lake)

**Key Findings:**
- Living area: Strong positive effect ($129/sqft increase, p < 0.001)
- Lake view: Premium of $249,000 over road view (p < 0.001)
- Age: Weak negative association (r = -0.075)
- Model explains 60.3% of price variation

**Model Performance:**
- R² = 0.603, Adjusted R² = 0.602
- F = 679.3 (p < 2.2e-16)
- All predictors except intercept significant at α = 0.05
- Residuals show acceptable normality and constant variance

### Model 2: Complete Second-Order Regression ⭐⭐ (Best Model)
**Predictors:** School rating, crime rate, school rating², crime rate², school rating × crime rate

**Key Findings:**
- Non-linear relationship between school rating and price (accelerating premium for top schools)
- Diminishing negative impact of crime at higher crime levels
- 81% of price variation explained by neighborhood quality factors
- Interaction term not significant (p = 0.283), but main effects and quadratic terms highly significant

**Model Performance:**
- R² = 0.809, Adjusted R² = 0.808
- F = 2272 (p < 2.2e-16)
- Strong fit without unnecessary complexity
- Residuals centered on zero with uniform spread

### Model 3: First-Order with Interaction
**Predictors:** School rating, crime rate, school rating × crime rate

**Performance:**
- R² = 0.800, Adjusted R² = 0.799
- F = 3573 (p < 2.2e-16)
- Slightly lower explanatory power than second-order model

## 📈 Correlation Analysis

**Strong Positive Correlation:**
- Living area sqft vs Price: r = 0.889 (very strong linear relationship)
- Larger homes command significantly higher prices

**Weak Negative Correlation:**
- Home age vs Price: r = -0.075 (minimal explanatory power alone)
- Age contributes little predictive value independently

**Non-Linear Relationships:**
- School rating vs Price: Accelerating upward curve (quadratic fit needed)
- Crime rate vs Price: Steep initial decline that flattens (quadratic fit needed)

## 💡 Business Value & Applications

**Real Estate Pricing Strategy:**
- Competitive list price suggestions for sellers
- Attractive pricing for buyers
- Help homes sell quickly without leaving money on the table

**Key Pricing Insights:**
- Location matters: Lake view adds $249K premium
- School quality has accelerating impact at higher ratings
- Crime's negative effect diminishes at already-high crime levels
- Living space is the single strongest price predictor

**Prediction Capabilities:**
- Point estimates for individual properties
- Confidence intervals for average prices in market segments
- Prediction intervals accounting for transaction variability

## 🎯 Example Predictions

### Scenario 1: Road View Home
**Specifications:** 2,150 sqft living, 1,050 sqft upper level, 15 years old, 3 bathrooms, backs to road

- **Point Prediction:** $456,828
- **90% Confidence Interval:** $440,088 - $473,569 (average for all similar homes)
- **90% Prediction Interval:** $233,663 - $680,093 (individual sale range)

### Scenario 2: Lake View Home
**Specifications:** 4,250 sqft living, 2,100 sqft upper level, 5 years old, 5 bathrooms, backs to lake

- **Point Prediction:** $1,074,285
- **90% Confidence Interval:** $1,045,117 - $1,103,454 (average for all similar homes)
- **90% Prediction Interval:** $852,523 - $1,296,048 (individual sale range)

### Scenario 3: High-Quality, Low-Crime Neighborhood
**Specifications:** School rating = 9.80, Crime rate = 81.02 per 100K

- **Point Prediction:** $874,500
- **90% Confidence Interval:** $863,900 - $885,300
- **90% Prediction Interval:** $721,600 - $1,027,400

### Scenario 4: Mid-Quality, High-Crime Neighborhood
**Specifications:** School rating = 4.28, Crime rate = 215.50 per 100K

- **Point Prediction:** $199,700
- **90% Confidence Interval:** $191,800 - $207,700
- **90% Prediction Interval:** $48,100 - $352,400

## 📊 Model Diagnostics

**Residual Analysis:**
- Residuals vs Fitted: No strong curvature, acceptable constant variance
- Normal Q-Q Plot: Minor tail deviations, adequate normality for inference
- Uniform spread across fitted values with slight widening at high prices

**Model Assumptions Met:**
- Linearity: Confirmed via residual plots
- Independence: Data from separate sales transactions
- Normality: Q-Q plots show acceptable normal distribution
- Homoscedasticity: Constant variance assumption reasonable

## 🔍 Nested Models F-Test

**Purpose:** Compare first-order and second-order models to determine if quadratic terms provide statistically meaningful improvement

**Conclusion:** Second-order model with quadratic terms significantly improves prediction accuracy over linear specification alone, justifying the additional complexity.

## 📁 Dataset Information

**Source:** King County, Washington housing sales dataset

**Sample Size:** 2,692 home sales

**Key Variables:**
- **Outcome:** `price` (final sale price in USD)
- **Physical characteristics:** `sqft_living`, `sqft_above`, `age`, `bathrooms`
- **Location factors:** `view` (road=0, trees=1, lake=2)
- **Neighborhood quality:** `school_rating`, `crime` (per 100K residents)

**Total Features:** 23 columns (quantitative and qualitative predictors)

## 📝 Statistical Methodology

**Analysis Workflow:**
1. **Exploratory Analysis:** Scatterplots and Pearson correlations to identify relationships
2. **First-Order Modeling:** Multiple regression with linear terms
3. **Second-Order Modeling:** Added quadratic terms to capture non-linear effects
4. **Model Comparison:** Nested F-tests to evaluate model improvements
5. **Validation:** Residual diagnostics and assumption checking
6. **Inference:** Confidence and prediction intervals for forecasting

**Key Statistical Tests:**
- **Overall F-test:** Tests if predictors collectively explain price variation
- **Individual t-tests:** Tests significance of each coefficient (α = 0.05)
- **Nested F-test:** Compares restricted vs full model specifications

## 🚀 Model Selection Rationale

**Recommended Model:** Complete Second-Order Regression (Model 2)

**Reasons:**
1. **Highest explanatory power:** R² = 0.81 vs 0.60 for first-order model
2. **Captures non-linearity:** Quadratic terms model accelerating/diminishing effects
3. **Statistically justified:** Nested F-test confirms quadratic terms improve fit
4. **Practical insights:** Reveals how school/crime effects change at different levels
5. **Good diagnostics:** Residuals show acceptable patterns for inference

## 💭 Key Insights

**Non-Linear Effects Matter:**
- Top-rated schools command exponentially higher premiums
- Crime's negative impact is strongest at low crime levels
- Linear models miss these important patterns

**Location Premium:**
- Waterfront properties (lake view) add substantial value
- View type alone worth $249K on average

**Size Dominates:**
- Living area square footage strongest single predictor (r = 0.889)
- Each additional sqft adds ~$129 to sale price

**Neighborhood Quality:**
- School ratings and crime rates together explain 80% of variation
- These factors more predictive than physical home characteristics alone

## 🎓 Statistical Concepts Demonstrated

- Multiple linear regression
- Polynomial regression (second-order models)
- Interaction effects
- Model comparison via nested F-tests
- Confidence vs prediction intervals
- Correlation analysis
- Residual diagnostics
- Hypothesis testing (F-tests, t-tests)
- R² and adjusted R²
- Feature engineering

## 👨‍💻 Author

**Kyle Payne**  
Data Analyst | Machine Learning | Statistical Modeling  
[LinkedIn](https://linkedin.com/in/kyle-payne-68408812a/) | [GitHub](https://github.com/kylepayne0110)

---

*This project demonstrates multiple regression modeling, feature engineering, model comparison, and statistical inference for real estate price prediction applications.*
