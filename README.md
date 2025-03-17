# UK Financial Sanctions List - Data cleaning & transformation

# Overview

In this notebook, we process and prepare the UK Financial Sanctions List for comparison against bank customer records. The dataset is extracted, partially cleaned, and structured to ensure accurate and thorough matching. The raw data has information on individuals, entities and ships.

# Workflow 

- **Initial Data Exploration:** Exploring the dataset to get a sense of its size, shape, contents and any potential issues
- **Data Reshaping:** Modifying the structure of the data by deleting unnecessary columns, merging columns, and grouping rows
- **Data Repurposing:** Repurposing information for different columns (addressing some missing values)
- **Data Cleaning & Formatting:** Ensuring consistent formatting, fixing typos, removing invalid entries etc

# Requirements

Ensure you have Python 3.12 as well as the following libraries installed:
- numpy
- pandas
- jupyter
- nltk

# Instructions

1. Download the dataset from (https://www.gov.uk/government/publications/financial-sanctions-consolidated-list-of-targets/consolidated-list-of-targets) in csv format.
2. Donwload *sanctions_preprocessing.ipynb* from this repository and place it in the same directory as the dataset.
3. Open a terminal and run jupyter notebook (this will launch jupyter).
4. In the jupyter interface, navigate the correct folder and open the ipynb file.
5. Under the section "Data Setup & Import", edit the file path to match the location of your csv file.
6. Run all cells in the notebook. The notebook will generate a new file with the output *output_data.csv*.


# Formatting Rules
The following rules were used to clean different data columns:

## Countries

- **No abreviations**:
  - 'United Kingdom' instead of 'UK' 
- **Simplified name version**:
  - 'North Korea' instead of 'Democratic People's Republic of Korea'
  - 'Bosnia Herzegovina' instead of 'Bosnia and Herzegovina'
- **'Republic of' Removed When Possible**:  
  - 'Moldova' instead of 'Republic of Moldova'  
  - 'Democratic Republic of the Congo' remained unchanged to avoid confusion with 'Republic of Congo'  
- **Hyphens Removed**:  
  - note that this might be problematic when distinguishing between:  
    - 'South Sudan' / 'Sudan'  
    - 'Guinea' / 'Guinea-Bissau' / 'Equatorial Guinea'

## Dates
  - **International Date format (ISO 6801):** yyyy-mm-dd

## Individual Names
-  Capitalized on the first letter only: 
   - 'Abdul'
- Every word seperated by comma: 
   - 'Abdul, Hai, Hazem, Qader'
- Hyphens and apostrophes preserved
- No parenthesis

## Entity & Ship Names
- CAPITALIZE: 
   - 'ABU NIDAL ORGANISATION'
- Full entity name separated by comma: '
   - 'ABU SAYYAF GROUP, AL HARAKAT AL ISLAMIYYA'
- Hyphens and apostrophes preserved
- Acronyms preserved
- No parenthesis
- Short abreviations: CO, LTD, INC


# Final Output

At the end the data was condensed to have one row for each Group ID and the following columns:
- Sanctions related columns:
    - Group ID, Group Type, Last updated, Regime
- Target specific columns:
    - Name(s), Date of Birth, Countries, Address(es), Phone Number, Name Non-Latin Script

The following columns were not standardized:
- Regime, Address(es), Phone number, Non-Latin Script

  



















  
