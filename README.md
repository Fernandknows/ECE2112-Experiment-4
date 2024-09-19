# EXP4 - Data Wrangling and Data Visualization <br/> *Christian Justin M. Fernando | 2ECE-B | ECE2112*
Hello! This repository contains Python codes I made for my ECE2112 course, particularly for Experiment #4. <br/><br/> 
# For experiment #4 the **instructions** are:

**1.** Download the ECE Board Exam 2 dataset found on this link: bit.ly/ECEBoardExamDataset <br/>
**2.** Write a Python script/code in the Jupyter Notebook to do the given problems. <br/>
**3.** Submit your Jupyter notebook in the dedicated submission bin. <br/>

#### Important note: The problem outputs can be seen inside my `.ipynb` files. You can also use my `.py` executable files which leads you directly to a specific problem. 

# ECE Board Exam Problem - Part 1 <br/>

Using data wrangling and data visualization techniques with storytelling, analyze the data and present different (i) data frames and (ii) visuals using the dataset given.  

##### Access the Pandas Library

Use `import pandas as pd` to access the pandas library. Run the data frame by assigning a variable for it and printing it. Before running, make sure you have downloaded the ECE Board Exam 2 dataset, if not, kindly refer to instruction #1.

```python
#Access the pandas library.
import pandas as pd

#Read and import `xlsx` file into a data frame.
dframe = pd.read_excel('board2.xlsx')
frame
```

##### a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown is Luzon  

```python
#Storing the organized data frame into Instru with set parameters.
Instru = dframe[(dframe['Track'] == 'Instrumentation')
                &(dframe['Hometown'] == 'Luzon')
                &(dframe['Electronics'] >70)][['Name', 'GEAS', 'Electronics']]
Instru
```

##### Save this file using the syntax below:
```python
#Test case to save the file and verify the created output.
Instru.to_excel('Intsru.xlsx', index=False)
```

The purpose is so that we can just print `Instru` if it is needed, and to verify whether the output data is complete and organized.

##### b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender is Female  

```python
#Creating a new column called 'Average' inside the original data frame.
dframe['Average'] = dframe[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

#Storing the organized data frame into Mindy with set parameters.
Mindy = dframe[(dframe['Hometown'] == 'Mindanao') 
                &(dframe['Gender'] == 'Female') 
                &(dframe['Average'] >=55)][['Name', 'Track', 'Electronics', 'Average']]
Mindy
```

##### Save this file using the syntax below:

``` python
#Test case to save the file and verify the created output.
Mindy.to_excel('Mindy.xlsx', index=False)
```

The purpose is so that we can just print `Instru` if it is needed, and to verify whether the output data is complete and organized.

<br/>

**Data and Results Discussion:** In this problem, importing Pandas as pd is crucial. This is declared to be able to access the core library for Python Data Analysis; used for working with data sets.

For **part a**, it demonstrates how to utilize the Pandas library to analyze data from an Excel file. First, it imports the library and reads an Excel file named `board2.xlsx` into a data frame called `dframe`. Next, it filters this data frame to create a new one, `Instru`, which includes only the rows where the 'Track' is 'Instrumentation', the 'Hometown' is 'Luzon', and the 'Electronics' score exceeds 70. Finally, it selects only the relevant columns: 'Name', 'GEAS', and 'Electronics', resulting in a focused data frame that highlights individuals from Luzon with expertise in Instrumentation and strong Electronics performance. 

For **part b**, this code continues the data analysis process by enhancing the original data frame called `dframe`. First, it creates a new column called 'Average' that calculates the mean of the scores from the 'Math', 'Electronics', 'GEAS', and 'Communication' columns for each row. This is achieved using the mean() function with axis=1, which indicates that the mean should be calculated across the specified columns for each individual.

Next, the code filters the data frame to create a new data frame named `Mindy`, which includes only the rows where the 'Hometown' is 'Mindanao', the 'Gender' is 'Female', and the 'Average' score is 55 or higher. The resulting `Mindy` data frame consists of the selected columns: 'Name', 'Track', 'Electronics', and 'Average'. This refined data frame highlights female individuals from Mindanao who meet the specified criteria, providing insights into their academic performance and specialization. 

<br/>

# ECE Board Exam Problem - Part 2

Create a visualization that shows how the different features contribute to average grades. Does a chosen track in college, gender, or hometown contribute to a higher average score?

##### Importing the necessary libraries
```python
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns
```

##### Creating the subplot to put multiple plots in one figure and assigning a value for the size of the figure
```python
fig, ax = plt.subplots(1, 3, figsize=(15, 5))
```

##### Point plot for average grade by track
```python
sns.pointplot(x='Track', y='Average', data=dframe, ax=ax[0], color='red')
ax[0].set(title='Average Grade by Track', ylabel='Average Grade', xlabel='Track')
ax[0].set_ylim(55, 80)  # Set y-axis limits
````

##### Point plot for average grade by gender
```python
sns.pointplot(x='Gender', y='Average', data=dframe, ax=ax[1], color='blue')
ax[1].set(title='Average Grade by Gender', ylabel='Average Grade', xlabel='Gender')
ax[1].set_ylim(55, 80)  # Set y-axis limits
```

##### Point plot for average grade by hometown
```python
sns.pointplot(x='Hometown', y='Average', data=dframe, ax=ax[2], color='green')
ax[2].set(title='Average Grade by Hometown', ylabel='Average Grade', xlabel='Hometown')
ax[2].set_ylim(55, 80)  # Set y-axis limits
```

##### Utilizing `tight_layout` to ensure automatic spacing adjustments
```python
plt.tight_layout()
```

##### Displaying all the figures and their plots.
```python
plt.show()
```
<br/>

**Data and Results Discussion:** <p>This part utilizes the Pandas, Matplotlib, and Seaborn libraries to visualize the average grades of students based on different categories. First, it imports the necessary libraries and calculates a new column, <code>'Average'</code>, in the original DataFrame (<code>dframe</code>), which computes the mean of the scores from <code>'Math'</code>, <code>'Electronics'</code>, <code>'GEAS'</code>, and <code>'Communication'</code> for each student. Next, it sets up a subplot structure to accommodate three separate plots within a single figure, defining the figure size for clarity.</p>

<p>The first plot displays the average grade by <code>'Track'</code>, using a point plot with red markers. The second plot illustrates the average grade by <code>'Gender'</code> in blue, while the third shows the average grade by <code>'Hometown'</code> in green. Each plot includes titles and labeled axes, with y-axis limits set between 55 and 80 to focus on relevant performance levels. Finally, the <code>tight_layout()</code> function is called to optimize spacing between the plots, and <code>plt.show()</code> is used to display the visualizations, allowing for a comprehensive comparison of average grades across different categories.</p>

**In the output**, you will see that based on the graph presented, it is evident that the various features—track, gender, and hometown—have a significant impact on students' average scores. The analysis of average grades by track reveals notable differences, suggesting that certain tracks may provide more effective educational support, which could enhance student performance. For Average Grade by Track, it can be seen that the Communication Track garnered the highest average grade, lying between 70 and 75. By Gender, it can be seen that they have the exact approximation of average grade, just above 70. However, some of the females garnered a lower value than the males. By Hometown, it can be seen that people from Luzon who took the ECE Board Exam garnered the highest average grade. Visayas comes 2nd, and Mindanao has the lowest average grade. The dots in the middle of each line indicate the mean grades of the board exam takers.


# About the author

The author is currently a second-year student pursuing a Bachelor's degree in Electronics Engineering. They have a strong passion for technology and are dedicated to applying their knowledge to real-world projects. In addition to their academic pursuits, the author continually seeks to expand their skill set. They are excited about the opportunities in the electronics field and aim to contribute to innovative solutions in the industry.

##### The problems above focus on Data Wrangling and Data Visualization. Feel free to let the author know if there is anything they can do to improve the code. Thank you!









