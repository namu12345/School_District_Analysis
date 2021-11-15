# School_District_Analysis
## Purpose of Analysis :
In this project I'll be helping Maria - Data Analyst from City School District to analyze the data for Student Funding and Student's standardized test scores. We'll be having Student data which includes Math & Reading scores as well as many other information in order to analyze the dataset which will help the School Board and Suprintendant to make decisions about School Budget and other priorities. 
In order to complete the School District Analysis here are the list of deliverables which we'll be working on :
- A high-level snapshot of the district's key metrics, presented in a table format
- An overview of the key metrics for each school, presented in a table format
- Tables presenting each of the following metrics:
    - Top 5 and bottom 5 performing schools, based on the overall passing rate
    - The average math score received by students in each grade level at each school
    - The average reading score received by students in each grade level at each school
    - School performance based on the budget per student
    - School performance based on the school size 
    - School performance based on the type of school

## Resources : 
- schools_complete.csv
- students_complete.csv

## Results :
The school board has notified Maria and her supervisor that the students_complete.csv file shows evidence of academic dishonesty; specifically, reading and math grades for Thomas High School ninth graders appear to have been altered. Although the school board does not know the full extent of the academic dishonesty, they want to uphold state-testing standards and have asked us to work on specifically Thomas High School 9th grade numbers. 

In order to scrutinize the Thomas High School 9th graders it was best to only replace their math and reading scores while keeping all other data associated with this student group intact.

Both math and reading scores were replaced with "NaN", which represents a "Not-a-Number" value, for 461 student records. Although this may seem like a significant number, these score replacements did not alter data summaries tremendously overall.

This is how i coded :

import numpy as np

ths_stu_data= student_data_df['school_name'] =='Thomas High School'

![image](https://user-images.githubusercontent.com/92283185/141699492-d9e54f6a-0e0b-41ab-a20d-11d918dcde3c.png)

student_data_df.loc[(ths_stu_data) & (student_data_df['grade']=='9th') ,'reading_score'] =np.nan

student_data_df.loc[(ths_stu_data) & (student_data_df['grade']=='9th') ,'math_score'] =np.nan

student_data_df.loc[ths_stu_data].sample(10)

and the output is :
![image](https://user-images.githubusercontent.com/92283185/141699428-f6834f3a-f155-4fc0-81c8-c0abbef681cb.png)

and the School & District summary snapshots are shown below : 

## School Summary : While calculating Per School Budget & per student budget output looks like this :

![image](https://user-images.githubusercontent.com/92283185/141699858-3b1fa550-a9e1-4c65-a2fc-f291cf0e4c4c.png)

## District Summary :

![image](https://user-images.githubusercontent.com/92283185/141699621-70748f7d-2d95-428e-a519-de515eda912c.png)

- And then when we calculate Thomas High School math and reading score excluding the 9th grade scores as they all are replace with NaN now, it give the following output :

![image](https://user-images.githubusercontent.com/92283185/141700508-9f7f6fbf-5508-48e1-9d01-f60809cada34.png)

- Another plus side from this data replacement is that it did not change the math and reading scores by grade. Granted, both the average math and reading score summaries were stratisfied by school and grade level. As shown above, the summary tables display "NaN" for ninth grade at Thomas High School whereas the remaining data remained intact.

## Math Score Grade-wise :

![image](https://user-images.githubusercontent.com/92283185/141701261-83c6f5a8-f0c3-48e2-af0a-b409f12b9eb9.png)

## Reading Score Grade-wise :

![image](https://user-images.githubusercontent.com/92283185/141701284-6395ca9f-02d4-4414-a84a-388e095fc97b.png)

- And here are the Top 5 & Bottom 5 Schools :

## Top 5 Schools :

![image](https://user-images.githubusercontent.com/92283185/141702036-86e9acae-d797-4a96-b08a-a18ace7b65a4.png)

## Bottom 5 Schools :

![image](https://user-images.githubusercontent.com/92283185/141702058-187b1071-db28-43af-84b4-e9fee2cba315.png)


