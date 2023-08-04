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
Using the AVG and STDEV functions, I calculated the average value and standard deviation for each listed column with numerical values. With these two values for each of the columns, I calculated the Pearson Coefficient for the percentage of zero-car households, the percentage of two or more cars households, and the total number of high-wage workers concerning the national walkability index for each of the Census regions. 
I calculated the Pearson Coefficient by finding the sum of the total value of the target column minus the average value, then multiplying this by the total value of the walkability index minus the average value. I divided this value by the column’s standard deviation multiplied by the walkability index’s standard deviation. 

The Results
As a result of my query, I found the Pearson Coefficient for the percentage of zero-car households and the national walkability index to be 0.3228, the Pearson Coefficient for two cars or more households to the national walkability index to be 0.3772, and the Pearson Coefficient for total high-wage workers to national walkability index to be 0.0007. 
The Pearson Coefficient ranges from -1 to +1, where +1 indicates a perfect positive linear relationship, -1 represents a perfect negative linear relationship, and 0 indicates no linear relationship. 
According to this equation, there is a strong positive correlation between the percentage of zero-car households and walkability, a strong negative correlation between the percentage of two-car or more households, and no correlation between high-income workers and walkability. 

This query calls the name of the Census area and the values for the columns representing the percentage of households with zero cars, the percentage of households with two cars or more, the total number of high-wage workers, and the national walkability index for the area. 
![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/2eb20d83-91f1-4529-963a-e1cbc47dad4c)

This query calls the average values for each of the listed columns. 
![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/af449647-c5a0-4c36-85e5-ac8a0241f3d5)
![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/34a524a8-56bb-4e39-9946-4845947803f6)
![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/24cb07ed-036f-4dc2-b96e-ea87163dddfd)
This query is used to derive the standard deviation for each of the columns. 
![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/13855b7c-f8de-4b7f-81b7-dc5fede66140)
![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/4c3e178f-6023-43b8-99fa-82d215fe6c96)
This query is used to declare the values for the averages and standard deviations for the listed columns.
![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/e91e7063-65e7-446a-b498-519f03731f0f)

![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/52e82f22-2be1-451d-a833-39498f84cdd9)

![image](https://github.com/jasghb11/carsandwalkability/assets/141364823/b761bcaf-1dcd-472b-ae28-727e700b2fc9)
