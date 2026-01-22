# Breakfast Cereal Analytics

### Project Overview

The breakfast cereal market offers numerous options, but insights into consumer preferences, nutritional metrics, and manufacturer performance are fragmented.

This project leverages Python for data preprocessing and exploratory analysis and Power BI for interactive visualization, producing a dashboard that provides actionable insights for manufacturers, retailers, and consumers.

### Project Objectives

1. Perform manufacturer- and product-level popularity analysis

2. Compare hot vs cold cereals for nutritional performance and market share

3. Evaluate key nutritional metrics: calories, protein, fat, fiber, sugar, sodium, potassium, and vitamins

4. Identify top-performing cereals and manufacturers

5. Develop an interactive Power BI dashboard with slicers, KPIs, and trend analysis

### Dataset Overview

Source: Cereal Nutrition Dataset – Kaggle

Prepared by: Petra Isenberg, Pierre Dragicevic, Yvonne Jansen

Granularity: Product-level

Format: CSV / structured tabular data

Dataset Fields:

| Variable | Type | Description |
|----------|------|-------------|
| Name | String | Cereal product name |
| mfr | Categorical | Manufacturer (A = American Home Food Products, G = General Mills, K = Kellogg’s, N = Nabisco, P = Post, Q = Quaker Oats, R = Ralston Purina) |
| type | Categorical | Cereal type (Hot / Cold) |
| calories | Numeric | Calories per serving |
| protein | Numeric | Protein content (grams) |
| fat | Numeric | Fat content (grams) |
| sodium | Numeric | Sodium content (milligrams) |
| fiber | Numeric | Dietary fiber (grams) |
| carbo | Numeric | Complex carbohydrates (grams) |
| sugars | Numeric | Sugar content (grams) |
| potass | Numeric | Potassium content (milligrams) |
| vitamins | Numeric | Percentage of FDA-recommended vitamins and minerals (0, 25, 100) |
| shelf | Numeric | Display shelf position (1 = bottom, 3 = top) |
| weight | Numeric | Weight of one serving (ounces) |
| cups | Numeric | Serving size in cups |
| rating | Numeric | Overall cereal rating |

### Technical Workflow

1. Data Preprocessing (Python)

Standardization & Cleaning:

Standardized manufacturer codes and cereal types

Handled missing or inconsistent nutritional values

Derived Metrics:

Total sugar per calorie (sugar/calories)

Fiber-to-calorie ratio (fiber/calories)

Popularity index based on rating and shelf position

Aggregation:

Manufacturer-level metrics (avg calories, fiber, sodium, popularity)

Hot vs Cold cereal comparison

Example Python Libraries Used: pandas, numpy, matplotlib, seaborn

2. Data Modeling (Power BI)

Fact Table: Cereal product-level nutritional and popularity metrics

Dimension Tables: Manufacturer, Type (Hot/Cold), Shelf, Vitamins Category

Relationships:

1:N relationships for Fact → Dimensions

Optimized for filtering, drill-through, and slicer performance

3. DAX Calculations

Dynamic KPIs:

Avg_Calories = AVERAGE('Cereal'[calories])
Avg_Fiber = AVERAGE('Cereal'[fiber])
Total_Sodium = SUM('Cereal'[sodium])


Hot vs Cold Metrics:

Avg_Calories_Hot = CALCULATE([Avg_Calories], 'Cereal'[type]="Hot")
Avg_Calories_Cold = CALCULATE([Avg_Calories], 'Cereal'[type]="Cold")


Top Manufacturer by Popularity:

Top_Manufacturer = 
  TOPN(
    1, 
    SUMMARIZE('Cereal','Cereal'[mfr],"Popularity",SUM('Cereal'[rating])),
    [Popularity],
    DESC
  )


Population-Level Nutritional Ratios:

Fiber per serving / Calories

Sodium per calorie

4. Dashboard Design

KPIs: Avg Calories, Avg Fiber, Top Manufacturer, Hot vs Cold Popularity

Visuals:

Bar charts: Manufacturer-wise ratings and nutrition comparison

Distribution plots: Sodium and sugar content across Hot/Cold cereals

Top 10 cereal products by rating

Filters & Slicers: Cereal Name, Manufacturer, Type

Executive Storytelling: Focus on nutritional trade-offs and market composition

### Key Insights

Market Composition:

7 major manufacturers dominate the cereal market

Cold cereals contribute 86% of total sodium

Popularity Trends:

Hot cereals slightly more popular (57%) than cold (43%)

High-fiber cereals like All-Bran Extra Fiber and Shredded Wheat rank top

Manufacturer Performance:

Nabisco: Most popular

Followed by American Home Food Products and Kellogg’s

Nutritional Insights:

Avg Calories: 106.9, Avg Fiber: 2.2g

Cold cereals tend to have higher sodium

Hot cereals show cleaner nutritional profiles

### Business Impact

Consumers: Make data-backed healthier cereal choices

Manufacturers: Identify reformulation opportunities (reduce sodium, increase fiber)

Product Teams: Optimize product positioning based on popularity and nutrition

Retailers: Improve shelf placement strategy

### Conclusion

This project demonstrates integrated Python data analysis and Power BI visualization, enabling product, manufacturer, and nutritional insights. Stakeholders can efficiently evaluate trends, nutritional trade-offs, and brand performance in the breakfast cereal market.
