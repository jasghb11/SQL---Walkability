# carsandwalkability
A SQL query discovering correlations between car ownership and walkability

Correlations to Walkability in Neighborhoods in the United States
Walkability measures how accessible an urban area is by foot. Areas with high walkability are generally complete living spaces in which individuals can easily access community resources such as  employment, healthcare, and food without using individual modes of transportation. 

High levels of walkability have been shown to positively impact human health, economic well-being, and environmental cleanliness. Due to walkability’s apparent benefits for an urban population, city planners and civic leaders have long sought ways to increase a metropolitan area’s walkability. 

Goal
I sought to measure the correlation of a neighborhood’s walkability with other urban characteristics, such as the ownership of cars and levels of high-wage workers in the region. I believe that identifying the correlation between walkability and other elements could help civic planners better understand the neighborhood markers that result from or possibly cause higher levels of walkability.  
I intend to use the equation for the Pearson Coefficient to measure the correlation between any two columns of data. The Person Coefficient is a mathematical equation universally accepted as an appropriate way to measure the mathematical relationship between datasets. 

The Dataset
For my SQL queries, I drew from the National Walkability Index, a public dataset from the EPA measuring the relative walkability of every Census block in the United States. The dataset measured many different characteristics of each Census block, such as the total population, total housing units, jobs per household, and the neighborhood’s walkability index. 
The walkability index is a metric the EPA determines through a weighted formula using the results of several different indicator rank scores. 

My Approach
First, I imported the data set into Microsoft SQL Server Management Tool to better view and manipulate the data set. I then isolated the columns representing values for the name of the Census region, the percentage of households with zero cars, the percentage of households with two or more cars, the total number of high-wage workers that lived in the Census region, and the national walkability index. 
Using the AVG and STDEV functions, I calculated the average value and standard deviation for each listed columns with numerical values. With these two values for each of the columns, I calculated the Pearson Coefficient for the percentage of zero-car households, percentage of two or more cars households, and the total number of high-wage workers concerning the national walkability index for each of the Census regions. 
I calculated the Pearson Coefficient by finding the sum of the total value of the target column minus the average value, then multiplying this by the total value of the walkability index minus the average value. I divided this value by the column’s standard deviation multiplied by the walkability index’s standard deviation. 

The Results
As a result of my query, I found the Pearson Coefficient for the percentage of zero-car households and the national walkability index to be 0.3228, the Pearson Coefficient for two cars or more households to the national walkability index to be 0.3772, and the Pearson Coefficient for total high-wage workers to national walkability index to be 0.0007. 
The Pearson Coefficient ranges from -1 to +1, where +1 indicates a perfect positive linear relationship, -1 represents a perfect negative linear relationship, and 0 indicates no linear relationship. 
According to this equation, there is a strong positive correlation between the percentage of zero-car households and walkability, a strong negative correlation between the percentage of two car or more households, and no correlation between high-income workers and walkability. 

![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/af449647-c5a0-4c36-85e5-ac8a0241f3d5)



SELECT *
FROM WalkCor;

-- Mean and Standard Deviation for Percentages of Zero Cars
SELECT AVG(PercentageZeroCar) AS average_PercentageZeroCar, AVG(PercentageTwoCar) AS average_PercentageTwoCar,
		AVG(HiWgWk) AS average_HiWgWk, AVG(NatWalkInd) AS average_NatWalkInd
FROM 
	WalkCor;

GO

SELECT STDEV(PercentageZeroCar) AS StdDev_PercentageZeroCar, STDEV(PercentageTwoCar) AS StdDev_PercentageTwoCar,
		STDEV(HiWgWk) AS StdDev_HiWgWk, STDEV(NatWalkInd) AS StdDev_NatWalkInd
FROM WalkCor;

-- Data for Percentage of Households with Zero Cars
DECLARE @Mean_PercentageZeroCar FLOAT = 0.328226;
DECLARE @StdDev_PercentageZeroCar FLOAT = 0.1519;

-- Data for Percentage of Households with 2+ Cars
DECLARE @Mean_PercentageTwoCar FLOAT = 0.569938;
DECLARE @StdDev_PercentageTwoCar FLOAT = 0.2197;

-- Data for # of High Wage Workers in the Area
DECLARE @Mean_HiWgWk FLOAT = 9.5416;
DECLARE @StdDev_HiWgWk FLOAT = 235.3702;

-- Data for National Walkability Index
DECLARE @Mean_NatWalkInd FLOAT = 9.5416;
DECLARE @StdDev_NatWalkInd FLOAT = 4.3739

-- Pearson Correlation Coefficient for Percentage of Zero Cars and Walkability
DECLARE @Zero_Walkability_Pearson FLOAT;
SELECT @Zero_Walkability_Pearson = SUM((PercentageZeroCar - @Mean_PercentageZeroCar) * (NatWalkInd - @Mean_NatWalkInd)) / 
(COUNT(*) * @StdDev_PercentageZeroCar * @StdDev_NatWalkInd)
FROM WalkCor;

-- Pearson Correlation Coefficient for Percentage of 2+ Cars and Walkability
DECLARE @Two_Walkability_Pearson FLOAT;
SELECT @Two_Walkability_Pearson = SUM((PercentageTwoCar - @Mean_PercentageTwoCar) * (NatWalkInd - @Mean_NatWalkInd)) /
(COUNT(*) * @StdDev_PercentageTwoCar * @StdDev_NatWalkInd)
FROM WalkCor;

-- Pearson Correlation Coefficient for High Wage Workers and Walkability
DECLARE @HiWgWk_Pearson FLOAT;
SELECT @HiWgWk_Pearson = SUM((HiWgWk - @Mean_HiWgWk) * (NatWalkInd - @Mean_NatWalkInd)) /
(Count(*) * @StdDev_HiWgWk * @StdDev_HiWgWk)
FROM WalkCor;

SELECT @Zero_Walkability_Pearson AS ZeroCarsWalkability_Pearson_Coefficient;
SELECT @Two_Walkability_Pearson AS TwoCarWalkability_Pearson_Coefficient;
SELECT @HiWgWk_Pearson AS HiWgWk_Pearson_Coefficient;
