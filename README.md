# MIDTERM LAB TASK 2
This portfolio demonstrates how to clean and prepare data using Power Query. The dataset is made up of several related tables, with cleaning techniques used to improve data quality and consistency before analysis.

## Task Description:
Company X would like to extract some useful information from the UnclenedDSJObs csv taken
from a Job Posting site available in Kaggle. There are a lot of columns available but focus only
on generating insights that will answer the following questions:
1. Which Job Roles pay the highest and least.
2. What size companies pay the best.
3. Where Job Roles or Job Titles pay the best and least in a specific state.
 

## Step-by-Step Process
### Step 1: Download and Load Data  
1. Download the dataset (Uncleaned_DS_jobs.csv)  
2. Open Excel  
3. Go to Data → New Query → Open File → Text/CSV  
4. Click Load and then Edit using Power Query Editor  

### Step 2: Duplicate Raw Data  
1. Right-click the dataset in the Queries pane  
2. Select Duplicate  

### Step 3: Clean Salary Data  
1. Select the Salary Estimate column  
2. Go to Transform Menu → Extract → Text Before Delimiter  
3. Type "(" and click OK  
4. Create two new columns: Min Salary and Max Salary  
- Select Salary Estimate column → Add Column Menu → Column from Examples → From Selections  
- Type the first min salary value and press Enter (all rows will auto-fill)  
- Rename the column to "Min Sal"  
- Repeat the process for Max Salary  

### Step 4: Add Role Type Column  
1. Go to Add Column Menu → Custom Column  
2. Rename the column to "Role Type"  
3. Use this logic:
- If Job Title contains "Data Scientist" → Assign "Data Scientist"  
- If Job Title contains "Data Analyst" → Assign "Data Analyst"  
- If Job Title contains "Data Engineer" → Assign "Data Engineer"  
- If Job Title contains "Machine Learning" → Assign "Machine Learning Engineer"
- Otherwise, assign "Other"  

5. Change the column type to Text  

### Step 5: Split Location Column  
1. Select the Location column  
2. Add a Custom Column with corrections:  
- If Location = "New Jersey" → Assign ", NJ"
- If Location = "Remote" or "United States" → Assign ", Other"
- If Location = "Texas" → Assign ", TX"
- If Location = "California" → Assign ", CA"  

3. Click OK, then select the new column  
4. Go to Transform → Split Column → By Delimiter (comma ",")  
5. Click OK  
6. Rename the second split column to "State Abbreviations"  
7. Check and replace incorrect values (e.g., "Anne Rundell" → "MA")  

### Step 6: Split Size Column  
1. Create two new columns: MinCompanySize and MaxCompanySize  
2. Use the same method as Salary Estimate to split values  

### Step 7: Handle Negative Values  
1. Filter out -1s from the Competitors column  
2. Filter out 0s from the Revenues column  
3. Remove -1s from the Industry column  

### Step 8: Clean Company Names  
1. Remove any extra characters or ratings after company names  

### Step 9: Copy Cleaning Steps as Proof  
1. Go to Home Menu → Click Advanced Editor  
2. Copy and save the code in your portfolio

### Step 10: Reshape and Group Data  
#### Group by Role Type  
1. Duplicate the raw data → Rename it as "Sal By Role Type dup"  
2. Select only Role Type, Min Salary, and Max Salary columns  
3. Change Min and Max Salary type to currency  
4. Multiply values by 1000 (Numbers Column → Standard → Multiply → Type 1000)  
5. Group rows by Role Type and get the average for Min and Max Salary  

#### Group by Company Size  
1. Create a reference of raw data → Rename it as "Sal By Role Size ref"  
2. Select only Size, Min Salary, and Max Salary columns  
3. Change Min and Max Salary type to currency  
4. Multiply values by 1000  
5. Group rows by Size and get the average for Min and Max Salary  


### Step 11: Merge State Mapping  
1. Click Unclean DS Jobs  
2. Right-click in the Queries pane → New Query → Open Workbook State Mapping  
3. Select the columns and click OK  
4. Select Uncleaned DS Jobs query  
5. Choose the State Abbreviation column in both queries  
6. Click Merge → Click OK  
7. Rename the merged column as "State Full Name"  
8. Remove nulls and blanks  



### Step 12: Group by State  
1. Create a reference of raw data → Rename it as "Sal By State ref"  
2. Select only State Full Name, Min Salary, and Max Salary columns  
3. Change Min and Max Salary type to currency  
4. Multiply values by 1000  
5. Group rows by State Full Name and get the average for Min and Max Salary  



### Step 13: View Query Dependencies  
1. Go to View Menu → Click Dependencies  
2. Check if all queries are correctly linked  


## Screenshots 

### Before Cleaning and Transformation (Raw) 👇
![Image](https://github.com/user-attachments/assets/6c8ebc71-f089-4474-9a65-038c26dacf7a)

### Advanced Editor 👇
![Image](https://github.com/user-attachments/assets/48507095-96e1-407c-ad71-33c14300c75d)

### After Cleaning and Transformation (Final Output) 👇 
![Image](https://github.com/user-attachments/assets/9c612847-5713-4b02-8a01-b8dabf2560ba)

### Sal by Role Type 👇
![Image](https://github.com/user-attachments/assets/19512048-98a0-42f8-be5f-e1d7b75808b4)

### Sal by Size
![Image](https://github.com/user-attachments/assets/1284e0ba-12f7-4caa-8f14-2a03d8186c68)

### Sal by State 👇
![Image](https://github.com/user-attachments/assets/85cece4a-00e7-4133-a926-63d7380a5df2)

### States 👇
![Image](https://github.com/user-attachments/assets/df845eb8-193e-46e5-b566-f5c73e7f0c31)

### Query Dependencies 👇
![Image](https://github.com/user-attachments/assets/9e91469f-ff52-48cc-947d-b7eb846fde79)
