# Shopify App Analysis

## Project Overview

This project analyzes the landscape of apps on the Shopify platform using data scraped from publicly available Shopify websites. The goal is to identify key factors that play into the success of a Shopify app using Power BI visualizations and analysis.

For each numbered part in this project, you will produce a page in a Power BI report. Each question itself should be a visualization. For each subquestion, take a screenshot of your entire screen to show your work.

## Data Overview

The **shopify.xlsx** dataset contains public data scraped from the [Shopify App Store](https://apps.shopify.com/). It includes 4 tables:

- **apps:** Details of the apps on Shopify apps marketplace
- **apps_categories:** Join tables to connect apps with categories
- **categories:** Categories of the apps. Each app has multiple categories
- **reviews:** Each review (row) contains information on user opinion about the related app (rating and comment). Also, it contains the response from the developer if present.

## Project Structure

### Part 1: App Landscape

Create a new sheet in your Power BI (`.pbix`) file called **App Landscape**. This section focuses on key statistics on the types of apps available.

**Tasks:**

1. **KPI Card** - Create a visual with a single number that counts the unique number of apps
   - Add it to your App Landscape sheet

2. **Line Chart** - Get the sum of the review count on the Y-axis, and the lastmod date on the X-Axis
   - **Important:** lastmod date should NOT be in "date hierarchy" format for your X-Axis

3. **Scatterplot** - Compare reviews_count (X-axis) against average rating (Y-axis)
   - Annotate your interpretation with an inserted **Text Box** next to this scatterplot

**Deliverable:** Screenshot of the completed App Landscape sheet

---

### Part 2: Reviews

Create a new sheet in your `.pbix` file named **Reviews**. This section focuses on analyzing user reviews and developer engagement.

**Tasks:**

1. **helpful_reviews Column** - Create a new column in the **Reviews** table using DAX
   - Formula: `rating * (1+helpful_count)`
   - Create a Card visual showing the average value of the `helpful_reviews` column

2. **developer_answered Column** - Create a new column in the **Reviews** table using DAX
   - Formula: 1 (or TRUE) if `developer_reply` is not blank; 0 (or FALSE) if blank
   - Create a scatterplot comparing:
     - Y-Axis: Average `rating`
     - X-Axis: Value of `developer_answered` column

**Deliverable:** Screenshots for each question

---

### Part 3: App Reviews

Create a new sheet in your `.pbix` file named **App Reviews**. This section combines app and review data to analyze developer performance.

**Tasks:**

1. **Create Relationship & Developer Ratings**
   - In the data model, create a new relationship between **Reviews** and **Apps** tables:
     - From: `app_id` column (Reviews table)
     - To: `id` column (Apps table)
     - Type: **Many-to-One** (Reviews → Apps)
   - Create a bar chart with:
     - X-Axis: `developer`
     - Y-Axis: `sum of rating`

2. **Helpful Reviews by Developer** - Create a new bar chart to avoid misleading results
   - X-Axis: `developer`
   - Y-Axis: Average of `helpful_review` column
   - *Note:* This corrects for apps with many low-star reviews

3. **Developer Responsiveness** - Identify the most responsive developers
   - Create a bar chart with:
     - X-Axis: `developer` (from apps table)
     - Y-Axis: `developer_answered` column (created in Part 2.2)
   - Add a **Filter** (visual-level) for rows where `reviews_count` > 500

**Deliverable:** Screenshots for each question

---

## File Structure

```
shopify-power-bi-project/
├── README.md                          # This file
├── shopify.xlsx                       # Source data file
├── shopify-app-analysis.pbix          # Power BI report file
├── Data/                              # Supporting data files
└── Result-Screenshots/                # Screenshots of completed visualizations
    ├── Part1_App_Landscape_1.png
    ├── Part1_App_Landscape_2.png
    ├── Part1_App_Landscape_3.png
    ├── Part2_Reviews_1.png
    ├── Part2_Reviews_2.png
    ├── Part3_App_Reviews_1.png
    ├── Part3_App_Reviews_2.png
    └── Part3_App_Reviews_3.png
```

## Requirements

- **Power BI Desktop** (latest version recommended)
- **shopify.xlsx** dataset
- Screenshot tool for documentation

## Getting Started

1. Open Power BI Desktop
2. Load the **shopify.xlsx** file
3. Create a new blank report (`.pbix` file)
4. Follow the tasks in each part above, creating sheets and visualizations as specified
5. Take screenshots after completing each task
6. Save your Power BI file as **shopify-app-analysis.pbix**

## Key DAX Formulas

### helpful_reviews (Part 2.1)
```
helpful_reviews = [rating] * (1 + [helpful_count])
```

### developer_answered (Part 2.2)
```
developer_answered = IF(ISBLANK([developer_reply]), 0, 1)
```

## Notes

- Ensure date hierarchies are disabled when needed for accurate X-axis representation
- Screenshot entire screens to document your work for each question
- Remember to take a screenshot for each subquestion as you progress
- Filter visualizations at the visual level only (not page or report level) when specified
- Maintain consistency in naming conventions across all sheets and columns

## Output

All completed Power BI sheets, visualizations, and supporting screenshots should be saved in this project folder for review and presentation.
