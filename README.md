# EXPERIMENT 4 - Data Wrangling and Data Visualization
Name: **Cruz, Kathryn Angel S.**  
Section: **2ECE-A** 
## Intended Learning Outcomes  
1. To identify the codes and functions needed in cleaning and visualizing data
2. To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization
## Instructions:  
> [!IMPORTANT]
> Download the ECE Board Exam 2 dataset found on this link: [bit.ly/ECEBoardExamDataset](url) and write a Python script/code in the Jupyter Notebook to do the given problems. You may submit your Jupyter notebook in the dedicated submission bin.

## **ECE BOARD EXAM PROBLEM**  
Using ata wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.  

## Solution  
### 1. Create the following data frames based on the format provided:
> **Example:**
> Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as **Visayas**

Output:
<p align="center">
  <img src="https://github.com/user-attachments/assets/2198065f-73a1-478f-b10c-67ab2d1474d4" alt="Vis Example"/>
</p>  

Import related libraries
```python
import pandas as pd
```
Reading the excel file named 'board2.xlsx' to be stored in the variable boards  
```python
boards = pd.read_excel('board2.xlsx')
boards
```
Where the result will be:  
<p align="center">
  <img src="https://github.com/user-attachments/assets/6f609365-44f6-4624-810e-d546163c9cde" alt="Vis Example"/>
</p>  

> [!NOTE]
> **File name:** Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon

Creating a DataFrame named 'Instru' by locating the constants and displaying the Name, GEAS, and Electronics grade more than 70  
```python
Instru = pd.DataFrame(boards.loc[(boards['Track']=='Instrumentation')&(boards['Hometown']=='Luzon')&(boards['Electronics']>70), ['Name', 'GEAS', 'Electronics']])
Instru
```
Where the result will be:
<p align="center">
  <img src="https://github.com/user-attachments/assets/3d07d25a-96dd-4df4-800d-21f18265fd9d", alt="Instru"/>
</p>  

> [!NOTE]
> **File name:** Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

Creating a new key 'Average'  
```python
boards['Average'] = round(boards[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1),2)
boards
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/ada06a5e-d623-4038-8b4a-f1dfd5e6125e", alt="Mindy"/>
</p>

Creating a DataFrame named 'Mindy' by locating the constants and displaying the Name, Track, Electronics, and and Average grade of greater than or equal to 55  
```python
Mindy = pd.DataFrame(boards.loc[(boards['Hometown'] == 'Mindanao') & (boards['Gender'] == 'Female') & (boards['Average'] >= 55), ['Name', 'Track', 'Electronics', 'Average']])
Mindy
```
Where the result will be:
<p align="center">
  <img src="https://github.com/user-attachments/assets/97796078-a248-499a-80b1-cfc01e3c52da", alt="Mindy_result">
</p>  

### 2. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?  
>[!NOTE]
> Boxplot was utilized in the given data because it effectiveely shows the distribution of data between multiple categories.
Importing necessary libraries to effectively create visualizations  
```python
import matplotlib.pyplot as plt
```
#### Boxplot Grouped by Track  
```python
import matplotlib.pyplot as plt
```  
<p align="center">
  <img src="https://github.com/user-attachments/assets/a87ab502-0c57-4dfe-bdb7-3aeef217ad3c", alt="Mindy_result">
</p>   

**The boxplot shows that the Microelectronics Track has the highest median and also the highest average grade, while the Instrumentation Track has the lowest median and the only track with an outlier, and the Communication Track with the lowest average.**

#### Boxplot Grouped by Hometown
```python
boards.boxplot(column='Average', by='Track')
```
<p align="center">
  <img src="https://github.com/user-attachments/assets/4ad59ecc-ac8a-4afb-9eb4-658aeeba2598", alt="Mindy_result">
</p>  

**The boxplot shows that students from Luzon generally performed better than students from Mindanao and Visayas because. Additionally, only Mindanao has an outlier in this graph.**  

#### Boxplot Grouped by Gender  
```python
boards.boxplot(column='Average', by='Gender')
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/57b53d28-d49c-481a-8cfb-c877ec821070", alt="Mindy_result">
</p>   

**The boxplot shows that female examinees has lower median but had the highest average. On thee other hand, male examinees has higher median but with an outlier.**
