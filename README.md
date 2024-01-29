# Brain Machine Interface
 
# Data Transformation Script for CSV Files

## Overview
This Python script is designed to automate the processing of CSV files for data analysis. The script filters, renames, and concatenates data based on specific criteria, making it suitable for preparing datasets for further analysis or reporting.

### Technologies Used
- **Python**: The primary programming language used for scripting.
- **Pandas**: A Python library for data manipulation and analysis.

## Purpose
The script's purpose is to transform data within multiple CSV files by applying a series of predefined operations. These operations include filtering rows based on success criteria, excluding specific columns, renaming remaining columns with a suffix, and concatenating these columns horizontally. This process prepares the data for more focused and efficient analysis.

## Input

### Input Folder
- The script processes all CSV files located in a specified input folder.
- Each CSV file should be structured with named columns, and contain the data you want to process.

### Expected Data Format
- The script expects CSV files with specific column names, including 'trial', 'discrim', 'success', and others as detailed below.

## Processing Steps

### Filtering
- Rows where the column 'success' is marked as 'TRUE' are selected for further processing.

### Columns Excluded
- The following columns are removed from each file:
  - 'trial'
  - 'discrim'
  - 'success'
  - 'failure reason'
  - 'time in homezone'
  - 'pull duration'
  - 'reward duration'
  - 'discrim_delay'
  - 'go_cue_delay'

### Renaming and Concatenating
- For each unique value in the 'discrim' column, the remaining columns are renamed by appending the respective 'discrim' value as a suffix (e.g., '_bOval').
- The renamed dataframes are then concatenated horizontally.

### Handling NaN Values
- Rows where all values are NaN (after column exclusion) are removed from each individual dataframe before concatenation.

## Output

### Output Folder
- Processed files are saved in a specified output folder.
- The output CSV files are named after the original files with an additional "_processed" suffix.

### Output Data Format
- The resulting CSV files will have columns corresponding to each unique 'discrim' value from the original datasets, minus the excluded columns.
- Column names are appended with the respective 'discrim' value.

## How to Use

1. Place your CSV files in the input folder.
2. Run the script by specifying the paths to your input and output folders.
3. Processed files will be saved in the output folder.

## Limitations
- The script is tailored for CSV files with a specific structure and may not work correctly with differently formatted files.
- It assumes that the 'discrim' column contains finite and manageable unique values.
