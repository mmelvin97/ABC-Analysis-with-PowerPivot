# ABC Analysis with Excel
## Project Overview
- ABC analysis conducted on sales data
- PowerPivot was used to handle the large set of data by using data model
- PivotTable and PivotChart were used for reporting

## Objective
1. Load the relevant dataset into the excel workbook
2. Create relevant PivotTables and PivotCharts/ Charts for ABC analysis
3. Summarize findings

## Method
### Step 1: Loading the relevant dataset into excel workbook using PowerPivot
- the datase is obtained from kaggle website, source: https://www.kaggle.com/flenderson/sales-analysis
- download the data and load it into the PowerPivot data model
- PowerPivot ribbon > Data Model > Manage > Get external data > From other sources > Excel files

![image](https://user-images.githubusercontent.com/53467152/156309875-329b5b78-e13d-4236-b1a1-e2ea1e074ef6.png)

- Create new column "Cost" by mulitplying "PriceReg" and "ItemCount" columns
- This column is used for ABC analysis

### Step 2: Using PivotTable to create relevant table for ABC analysis
- create PivotTable from Data Model
- Insert ribbon> PivotChart > From Data Model
- move 'SKU_Number' to rows, 'File_type' to filter, 'PriceReg', 'Itemcount' and 'Cost'(thrice) to Value
- filter the 'File_type' to Historical
- select the 'Cost2' to show value as running total in... and rename it ('Cumulative sum') to show the cumulative sum 
- sort the 'Cost2' from Largest to smallest
- select 'Cost3' to show value as % running total in... and rename it('Percent of Total') to show the percentage of cumulative sum over the grand sum 
- apply conditional formatting that will relay which of rows in what category (i.e A(red),B(yellow) or C(green))

![image](https://user-images.githubusercontent.com/53467152/156323239-8027406c-58c7-4011-9198-472de0a7203a.png)


- for advance reporting and chart copy the 'Percent of Total' into new worksheet
## Step 3: Create ABC report
- Create "Catergory column" adjacent to the 'Percent of Total" column
- Using IF Functions to categorize accordingly: =IF(AND([@[Percent of Total]]>0,[@[Percent of Total]]<0.6),"A",IF(AND([@[Percent of Total]]>=0.6,[@[Percent of Total]]<0.85),"B", IF([@[Percent of Total]]>=0.85,"C",)))
- Create the appropriate charts

![image](https://user-images.githubusercontent.com/53467152/156323205-6b49d51e-88b5-4df7-b59d-7e900ba0099e.png)

# Conclusion
Category A items is represented 21% from the overall items and 60% in term of value. Category B items is represented by 30% from the overall items and 25% in value. Category C items is represented 49% from the overall items and only 15% in value.





 
