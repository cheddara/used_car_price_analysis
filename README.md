
---

## 🎯 Objectives

A used-car dealership wants to understand:

- Which vehicle characteristics most strongly influence price  
- How accurately price can be predicted using available listing data  
- How these insights can support smarter inventory acquisition and pricing decisions  

**Data task definition:**  
Using numerical and categorical vehicle features, build and evaluate regression models that predict vehicle price and identify which attributes contribute most to valuation.

---

## 🔍 CRISP-DM Summary

### **1. Business Understanding**
Dealers need a data-driven way to understand what makes certain vehicles more valuable and to guide pricing and acquisition decisions.

### **2. Data Understanding**
The dataset includes ~60k vehicle listings with attributes such as year, mileage, manufacturer, fuel type, transmission, and drive type. Initial inspection revealed missing values and extreme price outliers (some above \$1B), requiring careful cleaning.

### **3. Data Preparation**
Key preparation steps included:
- Removing rows with missing or invalid price, year, or odometer values  
- Filtering unrealistic outliers (keeping prices between \$500–\$100,000)  
- Engineering `car_age` from vehicle year  
- One-hot encoding categorical variables  
- Creating training/testing splits  
- Ensuring all features were numeric for sklearn models  

### **4. Exploratory Data Analysis (EDA)**
Visualizations included:
- Distribution of used-car prices  
- Price vs. mileage  
- Price vs. car age  
- Price differences across top manufacturers  

Patterns were strong and intuitive:
- Newer and lower-mileage cars command higher prices  
- Certain manufacturers consistently price higher than others  
- Price distributions are right-skewed  

### **5. Modeling**
Three regression models were trained and evaluated using cross-validation:

- **Linear Regression**
- **Ridge Regression (Grid Search)**
- **Lasso Regression (Grid Search)**

RMSE was the primary metric because it measures error in dollars and penalizes large deviations.

### **Model Results**

| Model                       | CV RMSE | Test RMSE | Test R² |
|-----------------------------|---------|-----------|---------|
| Linear Regression           | 8,334   | 8,603     | 0.651   |
| Ridge Regression (Tuned)    | 8,335   | 8,603     | 0.651   |
| Lasso Regression (Tuned)    | 8,335   | 8,603     | 0.651   |

**Interpretation:**  
All models performed nearly identically. Regularization (Ridge, Lasso) provided no significant improvement, indicating stable features and low multicollinearity.  
**Linear Regression was selected as the final model** due to its simplicity and interpretability.

### **6. Evaluation**
The best model achieved:
- **Test RMSE ≈ \$8,600**  
- **R² ≈ 0.65**  

This means the model explains ~65% of the variation in used-car prices, which is strong given the inherent variability in listings (condition, trim, accidents, region, seller type).

The model generalizes well and provides actionable insight into the primary pricing drivers.

### **7. Deployment & Business Insights**

**Key drivers of price:**
- **Car age** (newer = more expensive)  
- **Mileage** (lower = higher price)  
- **Manufacturer** (brand value matters)  
- **Transmission, drive type, and fuel type** influence pricing by segment  

**Recommendations for the dealership:**
1. Prioritize acquiring **newer, lower-mileage vehicles** with strong resale brands.  
2. Use model estimates to guide **auction bidding and trade-in valuations**.  
3. Track additional variables (trim, vehicle condition, accident history) to further improve predictions.  
4. Apply insights to **optimize inventory mix** toward higher-value vehicle categories.

---

## 📈 Tools & Libraries Used

- Python  
- Jupyter Notebook  
- pandas, numpy  
- seaborn, matplotlib  
- scikit-learn (LinearRegression, Ridge, Lasso, GridSearchCV)  

---
## Visulas 

https://github.com/cheddara/used_car_price_analysis/blob/main/practical_application_II_starter/images/price_by_manufacture.png
https://github.com/cheddara/used_car_price_analysis/blob/main/practical_application_II_starter/images/price_distribution.png
https://github.com/cheddara/used_car_price_analysis/blob/main/practical_application_II_starter/images/price_vs_car_age.png
https://github.com/cheddara/used_car_price_analysis/blob/main/practical_application_II_starter/images/price_vs_mileage.png


## 📎 Notes

The dataset (`vehicles.csv`) is not included in this repository due to size restrictions but can be downloaded from the program’s provided resources or Kaggle.

---

## 👩‍💻 Author

**Annette
UC Berkeley ML & AI Professional Certificate  
Practical Application 11.1 Submission  
