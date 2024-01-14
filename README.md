# FIFA-2021-Dataset-Cleaning
- [Introduction](#Introduction)
- [Datasets](#Datasets)
- [Feature Selection](#Feature_Selection)






## Inroduction
* Drop Columns
    Absolutely, data cleaning is a crucial initial step in any data analysis or machine learning project. Clean and well-prepared data forms the foundation for accurate and reliable insights. Here's a general guideline for the data cleaning process:
    
    
    ## Datasets 
    The datasets used in Kaggle as a challenge to data cleaner interester , it provides manu information about each player since he joined his first club , age, tall , weight , height , and many lots of features that the player gain
    - **Data File** : [Fifa_Dataset](https://github.com/AbdallahOdeh2/FIFA-2021-Dataset-Cleaning/blob/c1d79745ee7f6eb875d748ca873aa34dfd384f36/fifa21%20raw%20data%20v2.csv)
    - **Data Source** : [Kaggle](https://www.kaggle.com/datasets/yagunnersya/fifa-21-messy-raw-dataset-for-cleaning-exploring/data?select=fifa21+raw+data+v2.csv)
    
    
    ## Feature Selection
    
    In the data cleaning process, I performed feature selection to streamline the dataset and focus on the most relevant information. The following columns were identified as unnecessary or not contributing significantly to the analysis:
    
    - `Short Name:` This column was dropped as it provides a shorter version of the player's name, which is redundant with the long name.
    
    - `PlayerURL and PhotoURL:` These columns were removed as they contain URLs that don't contribute meaningful information for analysis and modeling.
    
    - `Loan Date End:` The entire column was dropped due to a significant number of null values. Since the information about the end date of loans was incomplete, it was deemed not useful for the analysis.
    
    The feature selection process aimed to improve the dataset's clarity, focusing on the essential information relevant to the data analysis goals.
