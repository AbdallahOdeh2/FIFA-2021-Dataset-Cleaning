# FIFA-2021-Dataset-Cleaning
- [Introduction](#Introduction)
- [Datasets](#Datasets)
- [Feature Selection](#Feature_Selection)






## Inroduction

Absolutely, data cleaning is a crucial initial step in any data analysis or machine learning project. Clean and well-prepared data forms the foundation for accurate and reliable insights. Here's a general guideline for the data cleaning process:


## Datasets 
The datasets used in Kaggle as a challenge to data cleaner interester , it provides manu information about each player since he joined his first club , age, tall , weight , height , and many lots of features that the player gain
- **Data File** : [Fifa_Dataset](https://github.com/AbdallahOdeh2/FIFA-2021-Dataset-Cleaning/blob/c1d79745ee7f6eb875d748ca873aa34dfd384f36/fifa21%20raw%20data%20v2.csv)
- **Data Source** : [Kaggle](https://www.kaggle.com/datasets/yagunnersya/fifa-21-messy-raw-dataset-for-cleaning-exploring/data?select=fifa21+raw+data+v2.csv)


## Feature Selection
- Drop Column :
  
    In the data cleaning process, I performed feature selection to streamline the dataset and focus on the most relevant information. The following columns were identified as unnecessary or not contributing significantly to the analysis:
    
    - `Short Name:` This column was dropped as it provides a shorter version of the player's name, which is redundant with the long name.
    
    - `PlayerURL and PhotoURL:` These columns were removed as they contain URLs that don't contribute meaningful information for analysis and modeling.
    
    - `Loan Date End:` The entire column was dropped due to a significant number of null values. Since the information about the end date of loans was incomplete, it was deemed not useful for the analysis.
    
    The feature selection process aimed to improve the dataset's clarity, focusing on the essential information relevant to the data analysis goals.
  
- Handling Missing Data :
    the process also contain handling the missing values in dataset so, any null values consider as dirty data and it cleaned by drop it or filling it with the relative values
    - `Hits:`The column contained some missing values. To ensure data integrity and consistency, missing values in this column were imputed with a value of zero

- Dealing with Duplicates:
    Duplicate rows were carefully identified and removed from the dataset. This process ensured that each entry in the dataset is unique, preventing any potential distortions in the analysis results.
    and in this dataset there is no duplicates
  
- applying some formulas in Excel :
      1. **Substitute Function:**
         - Used the `SUBSTITUTE` function to replace euro signs or other unwanted characters in numeric columns.
      
          ```
          =SUBSTITUTE(A1, "€", "")
          ```
      
      2. **IF and ISNUMBER Functions:**
         - Employed the combination of `IF` and `ISNUMBER` functions to identify and handle numeric values while accounting for non-numeric entries.
      
          ```
          =IF(ISNUMBER(VALUE(A1)), VALUE(A1), 0)
          ```
      
      3. **Splitting 'Joined' Column into 'Start_Date' and 'End_Date':**
         - Utilized the `LEFT` and `RIGHT` functions to split a column, named 'Joined', into 'Start_Date' and 'End_Date'.
      
          ```
          Start_Date: =LEFT(A1, FIND("-", A1)-1)
          End_Date: =RIGHT(A1, LEN(A1)-FIND("-", A1))
          ```
- Create Functions in Python:
-   ```
    python
     Python Functions for Cleaning Numeric Columns
    
    When transitioning to Python, similar data cleaning operations can be performed using custom functions. Assuming you are working with a DataFrame using a library like Pandas:
    
    ```python
    import pandas as pd
    
    # Function to remove euro signs and unwanted characters
    def clean_numeric_column(value):
        return pd.to_numeric(str(value).replace('€', '').replace(',', ''), errors='coerce')
    
    # Function to split 'Joined' column into 'Start_Date' and 'End_Date'
    def split_joined_column(row):
        if '-' in str(row['Joined']):
            start_date, end_date = map(str.strip, str(row['Joined']).split('-'))
            return pd.Series({'Start_Date': start_date, 'End_Date': end_date})
        else:
            return pd.Series({'Start_Date': None, 'End_Date': None})
    
    # Apply functions to DataFrame
    df['Numeric_Column'] = df['Numeric_Column'].apply(clean_numeric_column)
    df[['Start_Date', 'End_Date']] = df.apply(split_joined_column, axis=1)







         
