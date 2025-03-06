# Batting Across the Bay: Analyzing the Rays’ Offensive Evolution at Steinbrenner Field

## Introduction

In the early hours of October 10th, as Hurricane Milton made its way across the state of Florida, the storm’s fierce wind and piercing rain tore to shreds the fiberglass dome of Tropicana Field, home of MLB’s Tampa Bay Rays. Tropicana Field, built in 1990, was due for replacement by 2028, but the damage rendered it unusable for the upcoming 2025 season. As the city of St. Petersburg, Pinellas County, and the Rays work to replace the fiberglass roof, the team will play their 2025 home games at George M. Steinbrenner Field. The stadium currently plays host to the New York Yankees for Spring Training and the Tampa Tarpons, the Single-A affiliate of the Yankees, during the minor league season. Besides being across Tampa Bay from the Rays' current home, the stadium’s field is also larger and most notably, outside.

Considering the Rays' shift from the domed, climate-controlled Tropicana Field to the outdoor Steinbrenner Field, exposed to the heat and unpredictable storms of south Florida, the problem I am considering is how this shift will impact the Rays’ performance at home. Of course, in a smaller, open-air stadium, the team may feel less of a home-field advantage, but more importantly, will this transition help or harm the team’s ability to score runs? This study examines how a different-sized stadium impacts the team as well as how playing so many more games under the hot Florida sun affects the team daily and over the course of the season.

## Methods

To predict the hit results of the 2024 Rays were they to play under the conditions of the 2024 Tampa Tarpons at Steinbrenner Field, I used an **XGBoost model**. I chose XGBoost because it iterates through different trials, focusing on errors, to output the best predictions under my given conditions. 

### **Data Collection**
- **Data Source:** Pitch-by-pitch data scraped from **Statcast**.
- **Filtering:** Home games for both **Rays** and **Tarpons** (bottom of the inning for batting analysis).
- **Focus Period:** Summer months **(June-August)** when weather may have the most significant impact.

### **Model Iterations**

#### **Model 1: Baseline**
- **Training Data:** Tarpons' home ball-in-play data (June-August).
- **Testing Data:** Rays' home ball-in-play data (June-August).
- **Features Used:**
  - x and y hit location
  - Trajectory (fly ball, ground ball, line drive, pop-up - dummy coded)

#### **Model 2: Adding Hit Characteristics**
- **Additional Features:**
  - Hit distance
  - Launch angle
  - Exit velocity
- **Missing Data Handling:** Replaced missing values with column means.

#### **Model 3: Including Weather Variables**
- **New Features Added:**
  - **Temperature**: Rays = constant 72°F (indoor), Tarpons = monthly averages.
  - **Wind Speed**: Rays = 0 mph (indoor), Tarpons = monthly averages.
- **Expanded Training Data:** Used **entire** Tarpons season instead of just June-August.

## Discussion

- As more **variables** and **training data** were added, the predicted hit outcome changes **stabilized**.
- **Outs increased** across all models, but primarily due to **singles turning into outs** rather than doubles or home runs.
- **Extra base hits increased**, likely due to:
  - **Stadium dimensions** (longer outfield fences)
  - **Outdoor conditions** (wind impact on batted balls)
- **Key Influencing Factors:**
  - **Launch angle** and **hit distance** played the biggest roles in determining hit outcomes.

## Recommendations

To adjust to Steinbrenner Field, the **Tampa Bay Rays should focus on:**
1. **Strength Training:** Improve power hitting to compensate for deeper fences.
2. **Optimizing Launch Angles:** Lower angles to prevent ground outs and maximize line drives.
3. **Weather Adjustments:** Practice hitting in varying wind conditions to acclimate to the open-air environment.

## Conclusion

While randomness plays a role in baseball outcomes, players can control certain aspects like **exit velocity** and **launch angle** to better adapt. Training regimens should be adjusted accordingly to **mitigate potential disadvantages** and **capitalize on new opportunities** at Steinbrenner Field.

---

## Bibliography

Zola, Todd. “Fantasy Baseball Impact of New Homes for Rays, Athletics.” *ESPN*, 18 Feb. 2025, [www.espn.com/fantasy/baseball](https://www.espn.com/fantasy/baseball).
