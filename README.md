# MIS-311 - Introduction to Business Analytics
## Part 1: Data Analysis and Insight (Dataset: 06 Student Performance)

I will use **Python** on ***Google Colab*** to process and analyze this dataset.  

### **1. Data Overview**  

---
<img width="452" height="477" alt="image" src="https://github.com/user-attachments/assets/57cb9290-719f-479f-8584-c5b77409eeaa" />   
  
<img width="335" height="127" alt="image" src="https://github.com/user-attachments/assets/da280fd1-7514-4718-8f5b-15b0b504c0f4" />    

---
The ***Student Performance*** dataset provides detailed information on students’ demographic backgrounds and their academic achievements across three subjects: math, reading, and writing. It contains **202 rows** and **8 columns**, where each row represents an individual student.

**Data Column Descriptions**
* race_ethnicity  (object): Different racial groups  
* parental_level_of_education (object): The educational background of the student's family  
* math_score (int): Performance in math  
* reading_score (int): Performance in reading  
* writing_score (int): Performance in writing skills
* total_score (int): The sum of math, reading, and writing scores
* average_score (float): The mean of the three subject scores

The dataset is designed to explore how factors such as gender, race ethnicity, and parental education influence student performance. It serves as a representative sample for analyzing educational outcomes and evaluating factors affecting student success.  

### **2. Data Cleaning**  
I will use `info()` function to check if there are any missing values. 

---
<img width="687" height="410" alt="image" src="https://github.com/user-attachments/assets/d5506365-92fd-4db0-86fc-b41071e2dc0e" />  

---
The ***parental_level_of_education*** column has **3** missing values.  
The ***average_score*** column has **4** missing values.  
The remaining columns have no missing values.  

The ***parental_level_of_education*** column I will fill "**not updated**" in the missing blank by using **fillna()** funtion. I decide to fill "**not updated**"  to ensure the ***descriptive statistics*** reflect the true state of the data, rather than using estimated values ​​that might misrepresent the original dataset.   

The ***average_score*** column is missing some spaces so I will calculate and fill in the blanks using the `fillna()` function.

---
<img width="1070" height="178" alt="image" src="https://github.com/user-attachments/assets/270bc40c-7e0d-43ce-a6e4-e831764fd791" />

---
After handling the missing values, ​​I will check again with the `info()` function

---
<img width="633" height="409" alt="image" src="https://github.com/user-attachments/assets/69551766-0266-47f6-86f1-db365463e20d" />

---
--> There is no missing value, all columns have 202 rows  

I will use `duplicated()` function to check if there are any duplicate rows.  

---
<img width="1275" height="355" alt="image" src="https://github.com/user-attachments/assets/d46f0738-dcb3-4c91-8ba3-70e3b977957d" />

---
This output shows there are duplicate rows in the dataset. For example, rows 10 and 12, 54 and 55, 63 and 64 have the same values, so some student records repeat and should be removed for accurate descriptive statistics.  

I will use `drop_duplicates()` function to remove duplicate rows

---
<img width="1295" height="584" alt="image" src="https://github.com/user-attachments/assets/cc3b33f8-76c9-4fc3-a090-e3ba6bd1b8e7" />

---
After cleaning, the dataset now has **199** rows (3 duplicate columns removed) and 8 columns. This makes the data more precise and ready for further descriptive statistics or analysis.

### **3. Descriptive Statistics**  

I will get ***descriptive statistics*** by using `describe()` function, not including gender column and text columns, including them would not give useful descriptive statistics like mean, min, or max. Removing them helps focus on the numeric scores for clearer analysis.  

---
<img width="1065" height="432" alt="image" src="https://github.com/user-attachments/assets/a49db71f-dcfc-432f-a4a4-10acf199f198" />

---
This table shows descriptive statistics for students' scores in math, reading, writing, total score, and average score. On average, students scored between 64 and 67 points in each subject. Students score around 64.18 in math, 67.47 in reading, and 66.18 in writing, showing slightly stronger performance in reading. The minimum score is quite low, while the maximum score is 100, indicating a wide range of scores. The standard deviation (about 15-16) shows some variation in performance among students. Overall, the data shows average performance with some individual variation in achievement levels.  

***Insight 1***

I will compare students’ average scores across different parental education levels to see if parents’ education affects student performance.  I will use the `groupby()` and `mean()` functions to calculate the average score for each group.

---
<img width="922" height="429" alt="image" src="https://github.com/user-attachments/assets/a27353e5-da75-4dd9-a1d7-a2bfefb95978" />
<img width="1016" height="615" alt="image" src="https://github.com/user-attachments/assets/dec7bc3c-eadc-48c0-afe0-28b7f18857c4" />


---

The results showed that students whose parents had higher levels of education, such as bachelor’s or master’s degrees, tended to have higher average scores than other students. This suggests that parental education has a significant impact on children’s academic achievement. Understanding this can help schools and families provide appropriate support to help students from different backgrounds perform better in their studies.

***Insight 2***  

I will compare the average scores of students by race ethnicity to see if there are any differences in performance between these groups. I will use the `groupby()` and `mean()` functions to calculate the average score for each group.  

---

<img width="947" height="419" alt="image" src="https://github.com/user-attachments/assets/967f11d5-68f6-4673-82e1-6dacc104cc46" />
<img width="731" height="400" alt="image" src="https://github.com/user-attachments/assets/8c1c2bef-b1ea-4abc-86eb-0f1e66bdcfe5" />

---

The table shows that average scores vary across different race ethnicity groups. Group A has the lowest average score at 58.11, while Group E has the highest at 70.27. There is a clear upward trend from Group A to Group E, indicating that race ethnicity may be associated with differences in academic performance.

***Insight 3***  

I will compare the scores of 3 subjects across 2 different genders to see if gender affects academic performance in the subjects. I will use the `groupby()` and `mean()` functions to calculate the average score for each group.

---

<img width="810" height="230" alt="image" src="https://github.com/user-attachments/assets/582abc1c-7cd3-416e-980c-8b38f1d6464d" />
<img width="717" height="550" alt="image" src="https://github.com/user-attachments/assets/b4836a1d-f0bc-4532-aae9-6b9f8b142c23" />


---
The data show that there is a difference in average scores between the two genders. The group with gender  0 (probably female) scored significantly higher in writing and reading, while the group with gender  1 (probably male) scored slightly higher in math. This suggests that female students tend to be stronger in language subjects, while male students are stronger in math. Overall, this difference reflects the gender differences in subject-specific learning.  


## **Conclusion**  

In summary, the results of the analysis show that many personal and social factors influence students' academic achievement. Parental level of education, gender, and race ethnicity groups are all associated with different mean scores across groups. Specifically, students with more educated parents tend to score higher, girls are stronger in language while boys are stronger in mathematics, and mean scores tend to increase across race ethnicity groups from A to E. These insights highlight the importance of providing appropriate academic support policies to reduce the learning gap between different groups of students.















