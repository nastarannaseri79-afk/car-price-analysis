# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)

# Car Price Analysis

## Project Overview

This project uses Python and exploratory data analysis (EDA) to investigate patterns and relationships in car prices.

The analysis examines how car prices are associated with vehicle characteristics such as engine size, curb weight, horsepower, dimensions, fuel efficiency, cylinder number, drivewheel, fuel system, body type and car make.

The project applies data inspection, cleaning, transformation, statistical correlation analysis and data visualisation to identify important patterns in the dataset and compare the relative strength of relationships with car price.

A particular focus of the analysis is on the vehicle characteristics that show the strongest relationships with price. The analysis also compares low-price and high-price vehicles to investigate whether selected characteristics can help distinguish between different price groups.

The findings describe associations within the available dataset rather than causal relationships.

---

## Dataset Content

The project uses the provided car price dataset stored as `CarPrice_Assignment.csv`. The dataset contains 205 car records and 26 variables describing vehicle characteristics, specifications, performance and price.

The target variable for this analysis is `price`.

Important variables include:

| Variable | Description |
|---|---|
| `CarName` | Car manufacturer and model name |
| `fueltype` | Fuel type |
| `aspiration` | Aspiration type |
| `doornumber` | Number of doors |
| `carbody` | Vehicle body type |
| `drivewheel` | Drivewheel configuration |
| `enginelocation` | Engine location |
| `wheelbase` | Wheelbase |
| `carlength` | Car length |
| `carwidth` | Car width |
| `carheight` | Car height |
| `curbweight` | Vehicle curb weight |
| `enginetype` | Engine type |
| `cylindernumber` | Number of cylinders |
| `enginesize` | Engine size |
| `fuelsystem` | Fuel system |
| `boreratio` | Engine bore ratio |
| `stroke` | Engine stroke |
| `compressionratio` | Compression ratio |
| `horsepower` | Horsepower |
| `peakrpm` | Peak engine RPM |
| `citympg` | City fuel efficiency |
| `highwaympg` | Highway fuel efficiency |
| `price` | Car price |

The original dataset is retained as the source data. A working copy is used for preparation and analysis.

---

## Business Requirements

The main analytical requirement is to investigate the factors associated with car prices and identify vehicle characteristics that distinguish lower-priced and higher-priced cars.

The analysis aims to:

- Understand the distribution of car prices.
- Compare average prices between different car makes and models.
- Investigate price differences across vehicle categories.
- Identify numerical and categorical variables with strong relationships to price.
- Examine the characteristics of low-price and high-price vehicles.
- Investigate whether engine, performance, dimensions and fuel-efficiency characteristics show consistent relationships with price.

### Analytical Questions

The analysis addresses the following questions:

1. How are car prices distributed across the dataset?
2. Do average prices differ between car makes?
3. Which car models have the highest average prices?
4. Do prices differ across fuel type, body type and drivewheel?
5. Which vehicle characteristics have the strongest relationships with car price?
6. How are engine size, curb weight and horsepower related to price?
7. How does fuel efficiency relate to car price?
8. How do low-price and high-price vehicles differ in engine size, horsepower, curb weight and dimensions?
9. How does cylinder number differ between low-price and high-price vehicles?
10. Can selected vehicle characteristics help distinguish low-price from high-price cars?

---

## Rationale for Mapping Business Requirements to Data Visualisations

Different visualisation techniques were selected according to the type of relationship or comparison being investigated.

- **Distribution of car prices:** A histogram was used to examine the overall price distribution and identify concentration and skewness.

- **Average price by car make:** A horizontal bar chart was used to compare average prices across manufacturers.

- **Average price by car model:** A bar chart was used to highlight the highest-priced models in the dataset.

- **Price by vehicle categories:** Boxplots were used to compare price distributions across fuel type, body type and drivewheel.

- **Price-to-performance:** A histogram was used to examine the distribution of price per horsepower.

- **Correlation between variables:** A correlation heatmap and ranked correlation analysis were used to examine the strength and direction of relationships with car price.

- **Detailed numerical relationships:** Scatter plots were used to investigate relationships between price and engine size, curb weight, horsepower and highway MPG.

- **Pairwise relationships:** A pairplot was used to examine relationships between price and selected numerical vehicle characteristics.

- **Low-price versus high-price vehicles:** Boxplots were used to compare important numerical characteristics between the two price groups.

- **Cylinder number and price group:** A countplot was used to compare the distribution of cylinder configurations between low-price and high-price vehicles.

---

## Project Plan

The project follows a structured data analysis workflow:

1. **Extract** – Obtain the original `CarPrice_Assignment.csv` dataset.

2. **Load** – Load the dataset into Python using Pandas and inspect its dimensions, columns and data types.

3. **Clean** – Check for missing values, duplicate records, unsuitable identifiers and potential outliers.

4. **Transform** – Remove the car_ID identifier, split the CarName variable into car make and car model, encode categorical variables where required, and create additional analytical features

5. **Explore** – Use descriptive statistics and exploratory visualisations to understand car prices and vehicle characteristics.

6. **Visualise** – Use histograms, bar charts, boxplots, scatter plots, pairplots and correlation heatmaps to investigate the analytical questions.

7. **Analyse** – Interpret the visualisations and correlation results to identify the strongest relationships with car price.

8. **Compare** – Create low-price, middle-price and high-price groups using the 20th and 80th percentiles, then compare selected characteristics between the low-price and high-price groups.

9. **Conclude** – Summarise the main findings, discuss limitations and explain which characteristics appear most useful for distinguishing different price groups.

**Make Name Correction:** During the make-level analysis, inconsistent car make names were identified and corrected to ensure that vehicles from the same manufacturer were grouped correctly. Corrections included `maxda` → `mazda`, `porcshce` → `porsche`, `vokswagen`/`vw` → `volkswagen`, `toyouta` → `toyota`, and `Nissan` → `nissan`.
---

## Data Management

The original `CarPrice_Assignment.csv` dataset was retained as the source data and was not modified directly. A working copy was created in Pandas for inspection and preparation.

### Data Inspection

The dataset was inspected to understand:

- The structure and dimensions of the dataset.
- Column names and data types.
- Numerical and categorical variables.
- Missing values.
- Duplicate records.
- The distribution and validity of the data.
- The characteristics of the target variable, `price`.

The dataset contains **205 records and 26 variables**.

### Data Cleaning

Data-quality checks were performed before analysis.

The missing-value check found **no missing values**, so no imputation or row removal was required.

The duplicate-record check found **0 duplicate rows**, so no records were removed for duplication.

The `car_ID` column was removed because it is an identifier for individual vehicles and does not provide meaningful analytical information.

### Outlier Screening

Potential outliers in continuous numerical variables were assessed using the Interquartile Range (IQR) method.

Potential outliers were identified in several variables. The largest number of potential outliers occurred in compression ratio and stroke. The `price` variable contained **15 potential outliers**, representing approximately **7.32%** of the observations.

The identified observations were retained because an IQR result indicates that a value is statistically unusual but does not demonstrate that the observation is incorrect. In a car-price dataset, extreme values may represent genuine differences between standard, high-performance and expensive vehicles.

---

## Feature Engineering

Two additional analytical features were created during the analysis.

### Price-to-Performance Feature

A new feature called `price_per_horsepower` was created:

`price_per_horsepower = price / horsepower`

This feature provides an additional way to examine the relationship between car price and engine performance by showing the price associated with each unit of horsepower.

### Price Groups

To support comparative analysis, cars were divided into three price groups using the 20th and 80th percentiles of the price distribution:

- **Low Price** – price at or below the 20th percentile.
- **Middle Price** – price between the two thresholds.
- **High Price** – price at or above the 80th percentile.

The detailed comparison focuses on the Low Price and High Price groups.

These groups are used for exploratory comparison and should not be interpreted as formal market classifications.

---

## Categorical Variable Encoding

Categorical variables were identified using their `object` data type and converted into numerical format using one-hot encoding with `pd.get_dummies()`.

An encoded copy of the cleaned dataset, `df_encoded`, was created so that the original cleaned dataset remained unchanged and readable.

The `drop_first=True` option was used to remove the first category from each categorical variable and reduce redundant dummy variables.

The encoded variables were stored as integers (`0` and `1`) using `dtype=int`.
---

## Car Make Data Preparation

For the analysis of average price by manufacturer, the car make was extracted from the `CarName` field.

Some inconsistent spellings and abbreviations were identified and corrected, including:

- `maxda` → `mazda`
- `porcshce` → `porsche`
- `vokswagen` → `volkswagen`
- `vw` → `volkswagen`
- `toyouta` → `toyota`
- `Nissan` → `nissan`

The corrected make names were then used to calculate average car prices by manufacturer.

---

## Analysis Techniques

Exploratory Data Analysis (EDA) was used to investigate car prices and their relationships with vehicle characteristics.

The following techniques were used:

- **Descriptive analysis** to understand the structure and distribution of the dataset.
- **Histograms** to examine the distributions of car price and price per horsepower.
- **Bar charts** to compare average prices by car make and identify high-priced models.
- **Boxplots** to compare prices across fuel type, body type and drivewheel.
- **Correlation analysis** to identify numerical and encoded categorical variables with strong relationships to price.
- **Correlation heatmaps and ranked correlation charts** to compare the strength and direction of relationships with price.
- **Scatter plots** to investigate detailed relationships between price and important numerical characteristics.
- **Pairplots** to examine several key numerical relationships together.
- **Price-group comparisons** to compare low-price and high-price vehicles.
- **Countplots** to examine cylinder-number distributions across price groups.

No predictive machine-learning model was developed. The predictive-analysis section is limited to exploratory comparison of price groups because predictive modelling is outside the scope of the techniques covered in this analysis.

---

## Key Findings

The exploratory analysis identified several important patterns in car prices.

- **Engine size** has the strongest positive correlation with car price among the selected numerical variables, with a Pearson correlation of approximately **0.87**.

- **Curb weight** also has a strong positive relationship with price, with a correlation of approximately **0.84**.

- **Horsepower** shows a strong positive relationship with price, with a correlation of approximately **0.81**.

- **Car width** has a strong positive correlation with price of approximately **0.76**, while **car length** has a more moderate positive correlation of approximately **0.68**.

- **Highway MPG** and **city MPG** show strong negative relationships with price, with correlations of approximately **-0.70** and **-0.69**, respectively. Higher fuel efficiency is generally associated with lower-priced vehicles in this dataset.

- Among encoded categorical variables, the four-cylinder indicator shows a strong negative relationship with price (approximately **-0.70**). Rear-wheel drive has a positive relationship (approximately **0.64**), while front-wheel drive has a negative relationship (approximately **-0.60**).

- The average-price analysis shows substantial differences between car makes. **Jaguar and Buick** have the highest average prices in the dataset, while **Chevrolet** has the lowest average price.

- At model level, the **Buick Regal Sport Coupe (Turbo)** has the highest average price among the top 10 models examined.

- Price distributions vary across fuel type, body type and drivewheel. Body type and drivewheel show greater variation in price than fuel type.

- High-price vehicles generally have **larger engines, higher horsepower, greater curb weight and greater car width** than low-price vehicles.

- High-price vehicles generally have **lower city and highway MPG**, indicating lower fuel efficiency compared with low-price vehicles.

- **Cylinder number** also differs between price groups. Four-cylinder vehicles are much more common in the low-price group, while higher-cylinder configurations are more common in the high-price group. Some cylinder categories contain few observations, so this finding should be interpreted with caution.

Overall, engine size, curb weight, horsepower, car width, fuel efficiency and cylinder number appear to be useful characteristics for distinguishing low-price and high-price vehicles in this dataset.

---

## Conclusions

The analysis shows that car price is strongly associated with several measures of vehicle size and performance.

Engine size, curb weight, horsepower and car width show the strongest positive relationships with price. In contrast, city and highway fuel efficiency show strong negative relationships.

The comparison between low-price and high-price vehicles supports these findings. Higher-priced vehicles generally have larger and more powerful engines, greater curb weight and wider bodies, while lower-priced vehicles generally show better fuel efficiency.

Cylinder configuration also appears to distinguish the two price groups, with four-cylinder cars more common among low-priced vehicles and higher-cylinder configurations more common among high-priced vehicles.

The analysis provides evidence that these characteristics are associated with differences in car prices within the dataset. However, the relationships represent associations rather than proof of causation.

No machine-learning predictive model was developed as predictive modelling is outside the scope of the techniques covered in this analysis.

---

## Limitations

- The dataset contains a limited number of observations and variables, so other factors that may influence car prices are not included.
- Correlation and visualisations demonstrate associations rather than causation.
- Some vehicle categories contain relatively few observations, which may affect comparisons.
- The price-group approach is based on percentile thresholds and is intended for exploratory analysis rather than formal market segmentation.
- The findings are specific to this dataset and should not automatically be generalised to the wider car market.
- Some categorical variables were analysed through encoded representations for correlation purposes; these correlations should therefore be interpreted carefully.
- Potential outliers were retained because they may represent genuine vehicles rather than data errors, but extreme observations may still influence some results.

---

## Challenges Faced

- Understanding the structure and meaning of the car-price dataset before analysis.
- Identifying and handling inconsistent car make names.
- Deciding how to treat the `car_ID` identifier.
- Assessing potential outliers without automatically removing genuine high-value vehicles.
- Selecting appropriate visualisations for different analytical questions.
- Interpreting correlations involving one-hot encoded categorical variables.
- Comparing low-price and high-price vehicles using meaningful characteristics.
- Avoiding causal interpretations when the analysis only demonstrates associations.

### How the Challenges Were Addressed

A structured workflow was followed to inspect, validate and prepare the dataset before analysis.

The original data was preserved while separate working and encoded datasets were created for different analytical purposes.

Potential outliers were investigated using the IQR method and retained where there was no evidence that they represented invalid data.

Different visualisation methods were selected according to the analytical question, and findings were compared across correlation analysis and multiple visualisations.

The interpretation consistently distinguishes between association and causation.

---

## Main Data Analysis Libraries and Technologies

- **Python:** Used as the main programming language for data analysis.
- **Pandas:** Used for loading, inspecting, cleaning, transforming and analysing the car-price dataset.
- **NumPy:** Used for numerical operations and creating price groups.
- **Matplotlib:** Used for charts and visualisations.
- **Seaborn:** Used for statistical visualisations including boxplots, heatmaps and pairplots.
- **Plotly:** Used for interactive histograms, bar charts, boxplots and scatter visualisations.
- **Jupyter Notebook:** Used to develop, document and present the data analysis.
- **Git and GitHub:** Used for version control and maintaining the project development history.

---

## AI Tools and Credits

### ChatGPT

ChatGPT was used as a supporting tool during the project to:

- Clarify assessment requirements and the project roadmap.
- Review code and suggest improvements where appropriate.
- Improve Markdown documentation and explanations.
- Refine the presentation of the analysis.
- Check the grammar and spelling of project notes.

### Copilot

Copilot was used to assist with writing and cleaning code.

All analysis decisions, results and interpretations were reviewed and validated by the project author.

---

## Acknowledgements

- **Code Institute** – Course materials, project template and assessment guidance.
- **Data Analytics course** – Support and feedback provided during the project.
- **Kaggle** – Car price dataset used for this analysis.
