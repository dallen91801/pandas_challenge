# pandas_challenge
Project Overview and Comparison of Requirements vs. Execution

This project required calculating various summary statistics from a school dataset, broken down by district, school type, school size, and student performance across different subjects and grades. The process involved working with Pandas to clean, manipulate, and aggregate data, with the goal of generating insights for district- and school-level performance analysis.

Below is a breakdown of the major sections of the project and the challenges encountered in each.

District Summary (20 Points)
Tasks: 
  - Calculate metrics like total schools, total students, total budget, average math/reading scores, and passing percentages for math, reading, and both.
  - Create a `district_summary` DataFrame.

Challenges: 
  - Merging Data: Combining student and school data while preserving key columns was tricky. The merge function required careful parameter choices (e.g., `how="left"` and `on` parameters).
  - Data Cleaning: Handling different data formats, like ensuring the budget or student ID columns were in numerical format, required cleaning operations.
  - Percentage Calculation: Calculating the percentage of passing students for math, reading, and both subjects required logical filtering and aggregation steps that weren’t trivial at first.

School Summary (20 Points)
-Tasks: 
  - Calculate school-level statistics such as total students, per capita spending, average scores, and passing percentages.
  - Create a `per_school_summary` DataFrame.

Challenges:
  - Complex Aggregations: Calculating metrics such as total students, average scores, and passing percentages involved multiple grouping and aggregation operations. Careful handling of school-specific data was necessary to avoid miscalculations.
  - Per-Student Spending: This required dividing total budgets by the number of students per school, which involved aggregating data at the school level. Mistakes in grouping or merging could easily distort results.

Highest- and Lowest-Performing Schools (5 Points Each)
- Tasks: 
  - Sort schools by `% Overall Passing` to identify the highest- and lowest-performing schools.
  - Save the top 5 and bottom 5 schools to `top_schools` and `bottom_schools` DataFrames, respectively.

Challenges:
  - Sorting Data: Sorting by derived columns like `% Overall Passing` required careful attention to ensure no errors were introduced due to missing or incorrectly calculated data.
  - Top/Bottom Selection: Identifying and displaying the correct top and bottom 5 schools was straightforward but required ensuring the sorting and filtering steps were correctly ordered.

Math and Reading Scores by Grade (10 Points Each)
- Tasks: 
  - Group the data by `school_name` and `grade`, then calculate the average math and reading scores.
  - Combine the results into `math_scores_by_grade` and `reading_scores_by_grade` DataFrames.

Challenges:
  - Grouping by Multiple Columns: Grouping by both `school_name` and `grade` and calculating averages required proper use of `.groupby()` and `.mean()`. Ensuring that the grouping columns were selected correctly was vital.
  - Combining Data: Once grouped, combining the data into a single DataFrame for each subject was challenging, particularly ensuring that no information was lost during the process.

Scores by School Spending (5 Points)
- Tasks: 
  - Use `pd.cut()` to bin data by spending ranges and calculate average performance metrics.
  - Create a `spending_summary` DataFrame.

Challenges:
  - **Binning and Categorization**: Correctly binning the schools by spending required the use of `pd.cut()`, which involved ensuring that the spending data was in the correct format (e.g., stripping out dollar signs and commas).
  - **Merging Binned Data**: After binning the schools, calculating averages for each bin required grouping operations that needed to be carefully implemented to avoid introducing NaN values.

Scores by School Size (5 Points)
- Tasks: 
  - Use `pd.cut()` to categorize schools by size and calculate average performance metrics.
  - Create a `size_summary` DataFrame.

Challenges:
  - Handling Data Types: Like with school spending, ensuring that the student count data was in numerical form (by stripping out commas, etc.) was critical.
  - Grouping by Size: Binning and grouping schools by size required ensuring that the size bins correctly categorized each school. Debugging potential issues around data loss or incorrect bin assignments was common.

Scores by School Type (5 Points)
- Tasks: 
  - Group `per_school_summary` by school type and calculate the average performance metrics for each type.
  - Create a `type_summary` DataFrame.

Challenges:
  - Missing Data: Ensuring that the `School Type` column was included in the `per_school_summary` DataFrame was a common issue. Failing to merge this data early on led to errors when attempting to group by `School Type`.
  - Aggregating Correctly: Calculating the averages by school type was straightforward once the data was correctly merged, but mistakes in the earlier steps could complicate this operation.

General Challenges and Difficulties:
- Data Merging and Cleaning**: A recurring challenge was merging the school and student data correctly. Small mistakes here (e.g., incorrect joins, merging on the wrong columns) could result in substantial data errors down the line. Ensuring consistent data formats (e.g., converting strings to numbers) was also a persistent issue.
  
- Handling Categorical Data: When grouping by categorical variables (e.g., school type or size), dealing with missing categories or incorrectly binned data caused issues. The deprecation warnings related to categorical grouping (e.g., `observed=True`) also added complexity.

- Sorting and Selection: Sorting by derived columns and selecting subsets (e.g., top and bottom performers) had to be carefully implemented. Errors in sorting could skew the results and impact subsequent analysis.

- Edge Cases: Handling edge cases such as missing data, NaN values, or categories with no data was another common difficulty. These cases required either cleaning or careful handling in aggregation functions.

Conclusion:
Overall, the project covered many essential data science skills, including data cleaning, grouping, aggregation, and visualization. Although there were challenges with data formats, merging, and handling categorical variables, overcoming these difficulties was instructive in deepening the understanding of working with real-world datasets.