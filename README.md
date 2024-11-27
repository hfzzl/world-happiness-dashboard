# World Happiness Report Data Analysis

This project involves working with datasets from the **World Happiness Report (WHR)** for the years 2019 to 2023. The objective is to load, combine, and clean the data to prepare it for further analysis.

---

## **Project Overview**

The project consolidates annual data from 2019 to 2023 into a single dataset, handles missing values, identifies duplicates, and extracts insights for specific countries or years. The processed data is saved for further exploration.

---

## **Requirements**

Data Source: https://www.kaggle.com/datasets/sazidthe1/global-happiness-scores-and-factors 

Ensure you have the following Python libraries installed:
- `pandas`
- `numpy`

You can install these packages using:
```bash
pip install pandas numpy
```

---

## **Code Workflow**

1. **Importing Libraries**  
   The script imports necessary libraries:  
   ```python
   import pandas as pd
   import numpy as np
   ```

2. **Loading Data**  
   For each year from 2019 to 2023, the respective CSV file is loaded. A new column, `year`, is added to each dataset:  
   ```python
   for year in range(2019, 2024):
       filename = f'/path/to/dataset/WHR_{year}.csv'
       data = pd.read_csv(filename)
       data['year'] = year
       data_list.append(data)
   ```

3. **Combining Data**  
   All yearly datasets are concatenated into one table for a unified view:  
   ```python
   all_data = pd.concat(data_list, ignore_index=True)
   ```

4. **Handling Missing Values**  
   The script checks for null values and identifies rows with missing values in the `healthy_life_expectancy` column:  
   ```python
   all_data.isnull().sum()
   all_data.loc[(all_data['healthy_life_expectancy'].isnull())]
   ```

5. **Extracting Data for Specific Countries**  
   Example: Extracting data for **State of Palestine**, which is only available for the year 2023:  
   ```python
   find_country = 'State of Palestine'
   all_data.loc[all_data['country'] == find_country]
   ```

6. **Checking for Duplicates**  
   The script checks and reports any duplicate rows:  
   ```python
   all_data.duplicated().sum()
   ```

7. **Saving the Processed Dataset**  
   The cleaned and consolidated dataset is saved to a CSV file:  
   ```python
   all_data.to_csv('WHR_2019-2023.csv', index=False)
   ```

8. **Previewing the Data**  
   Display the first five rows of the dataset:  
   ```python
   all_data.head(5)
   ```

---

## **Usage**

1. Replace the `filename` path with the actual file paths for your WHR datasets.
2. Run the script to load and process the data.
3. Use the output `WHR_2019-2023.csv` file for further analysis.

---

## **Output**

- **Link:** https://public.tableau.com/views/WorldHappiness_17327282762710/WorldHappiness?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link
![World Happiness](https://github.com/user-attachments/assets/e5a805cc-5cb0-4c8c-b8cc-d747fee07ad5)

--- 
