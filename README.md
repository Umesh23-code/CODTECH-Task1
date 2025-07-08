Name:Umesh Yadav<br>
Company:Codtech IT Solutions
ID:CT08DF2632
Domain:Data Analytics
Duration:5th June to 5th August 2025
Mentor:Neela Santosh Kumar

Overview of the Project
Dataset: hw_200.csv
This dataset contains height and weight data for 200 individuals. It has the following columns:

"Index" - Identifier

"Height(Inches)" – Height in inches

"Weight(Pounds)" – Weight in pounds
1. Data Cleaning
➤ Column Renaming
Renamed columns for clarity:

"Height(Inches)" → Height

"Weight(Pounds)" → Weight

df = df.withColumnRenamed("Height(Inches)", "Height") \
       .withColumnRenamed("Weight(Pounds)", "Weight")
➤ Null/Missing Value Check
No missing values found.

df.select([F.count(F.when(F.isnan(c) | F.col(c).isNull(), c)).alias(c) for c in df.columns]).show()

2. Descriptive Statistics
df.describe().show()
Metric	Height (in)	Weight (lbs)
Count	200	200
Mean	~67.95	~127.22
Std Dev	~1.94	~11.96
Min	63.43	97.90
Max	73.90	158.96

✅ This shows a fairly tight distribution with minimal outliers.

📊 3. Distribution Analysis
➤ Group by Height (Rounded)

df = df.withColumn("Height_Rounded", F.round("Height"))
df.groupBy("Height_Rounded").count().orderBy("Height_Rounded").show()
Insight: Most individuals are clustered between 67 and 70 inches in height.

4. Correlation Analysis
df.stat.corr("Height", "Weight")
Correlation: ~0.98
Strong positive linear correlation between height and weight — taller people tend to weigh more.

📄 5. Summary of Insights
#	Insight
The data is clean and contains no missing/null values.
Average height: ~67.95 inches, Average weight: ~127.22 pounds
Strong correlation (~0.98) between height and weight
Most heights lie between 67–70 inches
Distribution is normal-like; no extreme outliers
