# Final Year Stats Assignment
## Applied Linear Regression – Cattle Price Analysis

### Overview
This assignment applies multiple linear regression techniques to analyse the factors that drive cattle market prices. The dataset contains 115 livestock sales recorded by Wapello Livestock Sales in Wapello, Iowa, from mid-September 1999 to January 2000. The analysis was conducted using SAS (PROC REG and PROC CORR).

---

### Dataset
- **Observations:** 115 cattle sales
- **Dependent Variable (Y):** Price (in thousands of dollars)
- **Independent Variables:**
  - X1: Age
  - X2: Bred (whether the cow is bred)
  - X3: Angus (breed indicator)
  - X4: Frame size (large or small)
  - X5: Weight
  - X6: Conditioned (physical condition)
  - X7: Registered

---

### Analysis Outline

#### 1. Correlation Analysis (PROC CORR)
- Examined Pearson correlation coefficients between all variables
- Assessed multicollinearity among independent variables

#### 2. Full Model – Multiple Linear Regression
- Fitted a regression model using all 7 independent variables
- Tested overall model significance (F-test)
- Tested individual variable contributions (t-tests)
- Interpreted regression coefficients
- Assessed model fit diagnostics (Residual plots, RStudent, histogram)

#### 3. Backward Elimination
- Performed stepwise backward elimination at α = 0.05
- Removed variables one at a time: Angus → Bred → Registered → Weight
- Arrived at a reduced final model with 3 significant predictors

#### 4. Final (Reduced) Model
- Tested ANOVA for the reduced model
- Assessed lack of fit
- Checked VIF for multicollinearity
- Tested for serial autocorrelation (Durbin-Watson test)
- Interpreted final model coefficients and diagnostics

---

### Key Conclusions

#### Correlation
- Age has a **moderate negative correlation** with price (r = -0.527)
- All other predictors show **weak positive correlations** with price
- Low correlations among independent variables suggest **no serious multicollinearity**

#### Full Model
- The overall model is **statistically significant** (F = 9.84, p < 0.0001)
- The model explains **39.16%** of the total variation in price (R² = 0.3916)
- Only **Age** is individually significant (p < 0.0001); all other variables were not significant at α = 0.05
- Every additional year of age is associated with a **decrease of ~$38,711** in price

#### Backward Elimination
- After 4 elimination steps, the final model retained: **Age, Frame, and Conditioned**
- R² of the final model = **0.3571**

#### Final Model
**Price = 1151.52 – 36.73(Age) + 42.21(Frame) + 60.97(Conditioned)**

- **Age:** Each additional year decreases price by ~$36,733
- **Frame:** Large-framed cows sell for ~$42,206 more than small-framed cows
- **Conditioned:** Cows in good condition sell for ~$60,966 more than those not in good condition
- **VIF < 10** for all variables → multicollinearity exists but does not create problems
- **Lack of fit test:** p = 0.6566 → model is adequate for the data
- **Durbin-Watson = 1.433** → evidence of positive serial autocorrelation among errors

#### Model Diagnostics (Final Model)
- Residuals randomly scattered → linearity and constant variance assumptions met
- No outliers detected (all RStudent values within ±3)
- Errors approximately normally distributed (bell-shaped histogram)
- Adjusted R² = 0.3397 → model explains ~34% of variation after adjusting for complexity; indicates weak overall fit

---

### Tools Used
- **SAS** – PROC CORR, PROC REG
- Backward elimination with SLS = 0.05
- Diagnostic plots: Residual vs Predicted, RStudent, Q-Q plot, Cook's D, Leverage
