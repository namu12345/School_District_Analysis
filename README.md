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

## School Summary : 
- While calculating Per School Budget & per student budget output looks like this :

![image](https://user-images.githubusercontent.com/92283185/141699858-3b1fa550-a9e1-4c65-a2fc-f291cf0e4c4c.png)

## District Summary :

![image](https://user-images.githubusercontent.com/92283185/141699621-70748f7d-2d95-428e-a519-de515eda912c.png)

- And then when we calculate Thomas High School math and reading score excluding the 9th grade scores as they all are replace with NaN now, it give the following output :

![image](https://user-images.githubusercontent.com/92283185/141700508-9f7f6fbf-5508-48e1-9d01-f60809cada34.png)

- Another plus side from this data replacement is that it did not change the math and reading scores by grade. Granted, both the average math and reading score summaries were stratisfied by school and grade level. As shown below, the summary tables for Math & Reading Score Grade-wise display "NaN" for ninth grade at Thomas High School whereas the remaining data remained intact.

## Math Score Grade-wise :

![image](https://user-images.githubusercontent.com/92283185/141701261-83c6f5a8-f0c3-48e2-af0a-b409f12b9eb9.png)

## Reading Score Grade-wise :

![image](https://user-images.githubusercontent.com/92283185/141701284-6395ca9f-02d4-4414-a84a-388e095fc97b.png)

- And here are the Top 5 & Bottom 5 Schools :

## Top 5 Schools :

![image](https://user-images.githubusercontent.com/92283185/141702036-86e9acae-d797-4a96-b08a-a18ace7b65a4.png)

## Bottom 5 Schools :

![image](https://user-images.githubusercontent.com/92283185/141702058-187b1071-db28-43af-84b4-e9fee2cba315.png)

## School Spending Summary :

Further the question arised as how does school spending per student affect the school's average scores and passing percentages?  Solution to this will help the school board make decisions about the budget for the upcoming school year. For that we need to orgabize the data by spending ranges for the schools. 

Using the describe() method will help us determine the spending bins we should use, based on the descriptive statistics. We got the following output :

![image](https://user-images.githubusercontent.com/92283185/141905971-7b96404e-b752-4efc-88b9-26bccb2cb45d.png)

Based on the figures given by the .describe() method, spending ranges per student in the school district were determined: 

![image](https://user-images.githubusercontent.com/92283185/141907094-e013f17b-24f6-427d-b28a-aaed96596a20.png)

School that spent between <$584 appear to have the best-performing students in math and reading. So the schools which spent the lowest are the highest performing shcool in Math & Reading.

![image](https://user-images.githubusercontent.com/92283185/141912641-157cab7c-14ce-465b-9c24-1414deb6e229.png)

## Scores by School Size

Scores by school size were calculated by determining size ranges for all 15 schools in the district:

-Small (<1000) 
-Medium (1000-2000) 
-Large (2000-5000)

When considering School Sizes, "Large" Schools (Over 2,000 Students) have the lowest average scores and passing percentages. The difference in performance between "Small" and "Medium" Size Schools is negligible (approximately 1%). Interestingly, all District schools in this dataset are characterized as "Large" schools. This may be an indication that students in this district learn and perform better in smaller, more intimate settings.

![image](https://user-images.githubusercontent.com/92283185/141914350-0ff23bcf-4d8b-4546-8fa3-479036059549.png)

## Charter vs. District Schools

Charter schools generally performed better than District schools in this analysis. The top five schools with the highest overall passing percentages are all Charter schools, whereas the bottom five are all District Schools. Charter schools in this dataset were typically characterized as "Small" and "Medium" size schools. As seen in the DataFrame below, Charter schools have a 36% higher overall passing percentage than District schools.

![image](https://user-images.githubusercontent.com/92283185/141915823-6cdd9084-fe86-471d-884b-da625c349885.png)

## Summary
Unfortunately, it is not possible to determine the extent of the potential academic dishonesty or identify soecific indivuals to exclude from the dataset. As a consequence of this, the entire ninth grade of students from Thomas High School have had their scores omitted from the results. This is a suboptimal situation because a full set of data is ideal for creating the most accurate results.

Relacing the ninth graders' scores with NaN caused Thomas High School's overall passing percentages and average scores to plummet. The district as a whole has also had its average math and reading scores decrease, as well as the overall passing percentage for students. Furthermore, Thomas High School lost its placement as a top five school within this District. However, after updating the total student counts to exclude the Thomas High School ninth graders and omitting their scores from the dataset, Thomas High School regained its high average scores and retained its position as the number two school in the District. To view the full script, please open PyCitySchools_Challenge.ipynb in Jupyter Notebook.







