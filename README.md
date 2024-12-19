# Student Performance Factor Analysis
This repository is made to support a medium article: https://medium.com/@vaniaelvinaa/student-performance-factor-analysis-2a6eb02fd4d8
## How to use
1. Download this repository.
2. Open `StudentAnalysis.ipynb` using Jupyter Notebook or Google Collab.
3. Run all cells.
## Introduction
Exam scores are frequently used to measure students’ academic success. However, many factors contribute to a student’s performance. These factors include internal aspects, such as a student’s motivation level, and external aspects, such as family background and access to resources. In this project, we analyzed students’ performance by answering several research questions using a dataset from Kaggle. This dataset contains 20 variables, which are described in the table below.

![image](https://github.com/user-attachments/assets/a85d39db-7999-4908-99f7-2e43285019ab)

## Research Questions
`What is the average exam score of students based on their access to resources?`

We are interested in finding out how students’ scores vary with different levels of access to resources. To do this, we need to separate students based on their level of access to resources and calculate their average exam scores.

![image](https://github.com/user-attachments/assets/4d402004-245f-450d-b9e9-94fa460c3849)
![image](https://github.com/user-attachments/assets/619a952c-4b53-4067-a204-ff92cfd81295)

From the table and graph shown above, it is obvious that students with high access to resources have higher scores compared to students with medium and low access to resources. This means that high access to resources correlate with students high scores. However, it is important to note that high access to resources might not the cause of a student’s high score.

`Which type of school has the highest average exam score?`

There have been many debates about whether private schools are better than public schools, and vice versa. According to the dataset, private schools have the highest average exam scores, as shown in the table below. However, the difference is not significant, amounting to less than one point. Therefore, it can be concluded that attending either a private or public school does not have a significant effect on students’ exam scores.

![image](https://github.com/user-attachments/assets/04ba670c-18fa-4c57-b9c9-ac4bb022208d)

`What is the percentage level of parental involvement among students who improved their scores?`

Parental involvement can be an important factor on students performance. However, based on our finding, we found that more than a half of the students who shown improvement in their exam scores have medium parental involvement. This concludes that high parental involvement doesn’t necessarily contribute to students performance improvement.

![image](https://github.com/user-attachments/assets/71823974-1e67-43ea-989c-0662590e5f0d)

`How much is the average score of students in the top 1%?`

To find the average score of students in the top 1%, it is important to sort students based on their exam score first then take out the students in the top 1%.

```
# get amount of students in the top 1%
top = int(len(students) * 0.01)

# get students in the top 1%
top_students = students.head(top)

# calculate average exam score of students in the top 1% 
top_average = round(top_students["Exam_Score"].mean())

# display answer
print(f"Average exam score of students in the top 1% is {top_average}.")
```
![image](https://github.com/user-attachments/assets/5691e7e7-80bb-4e42-81de-e27b1b112644)

Using the code shown above, it was obtained that the average exam score of students in the top 1% is 87.

`Whats is the percentage of students in the top 1% based on their motivation level?`

Students’ motivation level can be an important factor in their performance. However, based on our findings, we discovered that more than half of the students in the top 1% have medium motivation level. This suggests that a high motivation level doesn’t necessarily contribute to high exam scores.

```
# get amount of students in the top 1% for each motivation level
motivation = top_students['Motivation_Level'].value_counts()

# create a pie chart
plt.figure(figsize=(4, 4))
wedges, texts, autotexts = plt.pie(motivation, autopct='%.0f%%', startangle=140, colors=colors, textprops={'fontsize': 10, 'color':'white'})
colors = ['#1f77b4', '#4d92d1', '#7ab0eb']
plt.title('Motivation Level Among the Top 1% Students', fontsize=10)
plt.legend(wedges, parental_involvement_counts.index, title="Motivation Level", loc="center left", bbox_to_anchor=(1, 0, 0.5, 1))

# display the chart
plt.show()
```
![image](https://github.com/user-attachments/assets/0f944d77-0789-4859-8260-59f0d3900094)

## Variables Correlation Analysis
In this research we also analyzed correlations between variables and we found some variables with strongest correlation to students exam scores as listed below:
1. Attendance
2. Hours_Studied
3. Access_to_Resources and Previous_Score
4. Parental_Involvement and Tutoring_Sessions

![image](https://github.com/user-attachments/assets/ba8848ea-8da3-4097-997e-dedcfdb5a53f)




## Conclusion
From this analysis, it can be concluded that:
1. Students with higher access to resources consistently achieved higher scores, with an average score of 68. This positive trend was further supported by a strong correlation between students resource access and their exam scores, indicating that increased access to resources leads to better scores. This relationship was also validated through hypothesis testing.
2. Attending either a private or public school does not have a significant effect on students’ exam scores.
3. Students in the top 1% is more likely to be male compared to female. There’s also no evidence that proportion of female students in the top 1% is higher than male students.
4. Increased parental involvement leads to higher scores. However, this doesn’t necessarily contribute to improving their exam scores from their previous scores.
5. Higher family income leads to higher students exam scores and students with high family income has the highest probability to be in the top 1% compared to other students.
6. Students attendance has the highest correlation to students exam scores, where students who have at least 80% attendance are more likely to score the average and higher exam score compared to students with less attendance.
7. Students study hours has the second highest correlation to students exam scores, where students who studied at least 20 hours are more likely to score the average and higher exam score compared to students with less study hours.
