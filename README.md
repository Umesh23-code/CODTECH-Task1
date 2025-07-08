Name:Umesh Yadav<br>
Company:Codtech IT Solutions<br>
ID:CT08DF2632<br>
Domain:Data Analytics<br>
Duration:5th June to 5th August 2025<br>
Mentor:Neela Santosh Kumar<br>

**Overview of the Project**<br>
Dataset: hw_200.csv<br>
This dataset contains height and weight data for 200 individuals. It has the following columns:<br>

"Index" - Identifier<br>

"Height(Inches)" – Height in inches<br>

"Weight(Pounds)" – Weight in pounds<br>
**1.Data Cleaning**<br>
➤ Column Renaming<br>
Renamed columns for clarity:<br>

"Height(Inches)" → Height<br>

"Weight(Pounds)" → Weight<br>

df = df.withColumnRenamed("Height(Inches)", "Height") \<br>
       .withColumnRenamed("Weight(Pounds)", "Weight")<br>
➤ Null/Missing Value Check<br>
No missing values found.<br>

df.select([F.count(F.when(F.isnan(c) | F.col(c).isNull(), c)).alias(c) for c in df.columns]).show()<br>

**2.Descriptive Statistics**<br>
df.describe().show()<br>
Metric	Height (in)	Weight (lbs)<br>
Count	200	200<br>
Mean	~67.95	~127.22<br>
Std Dev	~1.94	~11.96<br>
Min	63.43	97.90<br>
Max	73.90	158.96<br>

✅ This shows a fairly tight distribution with minimal outliers.<br>

📊**3.Distribution Analysis**<br>
➤ Group by Height (Rounded)<br>

df = df.withColumn("Height_Rounded", F.round("Height"))<br>
df.groupBy("Height_Rounded").count().orderBy("Height_Rounded").show()<br>
Insight: Most individuals are clustered between 67 and 70 inches in height.<br>

**4.Correlation Analysis**<br>
df.stat.corr("Height", "Weight")<br>
Correlation: ~0.98<br>
Strong positive linear correlation between height and weight — taller people tend to weigh more.<br>

📄 **5. Summary of Insights**<br>
#	Insight<br>
The data is clean and contains no missing/null values.<br>
Average height: ~67.95 inches, Average weight: ~127.22 pounds<br>
Strong correlation (~0.98) between height and weight<br>
Most heights lie between 67–70 inches<br>
Distribution is normal-like; no extreme outliers<br>
