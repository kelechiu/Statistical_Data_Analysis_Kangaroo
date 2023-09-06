# Statistical Data Analysis for Kangaroo
# 1.  Introduction

The transportation sector and highway vehicles account for 30% and 24% of  annual U.S. Greenhouse Gas emissions respectively. As countries strive to reduce fuel consumption and air pollution caused by vehicles, the automotive industry has adopted technological measures to improve the fuel economy (measured as miles per gallon) of vehicles and promote a sustainable environment.

Some of these technological changes include the development of alternative fuel vehicles like electric cars; and modifications to the weight and power of vehicles to reduce fuel consumption and greenhouse gas emissions

By utilizing various statistical methods, this paper aims to examine the effects of vehicle characteristics such as engine size, transmission type and driving conditions on fuel economy and air pollution. Specifically, it aims to critically analyse the dataset and answer the following business questions:

1.	What type of car exhibits the most fuel economy?
2.	What type of car is environmentally friendly?

### Null Hypothesis

H01: There are no significant differences in fuel economy among different car types. 
H02: There are no significant differences in CO2 emissions among different car types.
### Alternative Hypothesis
H1: There are significant differences in fuel economy among different car types.
H2: There are significant differences in gas emissions among different car types.



# 2.  Dataset and Data Preparation
## 2.1.  Dataset Description
The dataset was derived from the fuel economy guide which is an affiliate of the U.S. Department of Energy (DOE). After downloading the dataset, it was imported into IBM SPSS for data preparation and analysis. The dataset has 729 rows and 19 columns, with each row describing the characteristics and features of the “carline”. According to the dataset’s source, Combined FE (Combined fuel economy) is measured in miles per gallon of fuel (MPG). CombinedFE represents a combination of highway driving (45%) and city driving (55%) (fuel economy, 2015). For the purposes of this research, CombinedFE is the preferred dependent variable that will be tested for fuel economy and Combined CO2 will be tested for environmental friendliness among different car types.

## 2.2.  Data Preparation Methods 
This is the process of transforming data into a clean and consistent format for further analysis. It involves cleaning, validating and transforming the data to ensure the quality of the dataset is accurate, complete and aligned with the goals of the analysis. Some of the key methods of data preparation used in this analysis are explained below:

### 2.2.1.  Missing Values
It is important to handle missing values in datasets to avoid incorrect or biased analysis results. 
As seen from Figure 2 below, there are no missing values in the dataset.

<img width="165" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/a9de9245-42c5-4893-afc3-36d335dd4b41">

### 2.2.2.  Duplicate Values
Duplicate values in datasets can skew statistical calculations and lead to biased/ incorrect descriptive statistics like mean, mode and standard deviation. As seen in Figure 3 below, there are 7 duplicate values in the dataset, so I investigated the dataset and identified the nature of the duplicates before deciding how to handle them. Figure 4  displays the duplicated values and their primary values, and Figure 5 confirms the absence of duplicates in the dataset after I deleted them. After deleting the 7 duplicated values, there are now 722 rows/records in the dataset.

<img width="367" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/72c6362f-bbd8-4faa-9b81-d6d8cfac5216">
<img width="409" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/38d0e686-d1c8-4bea-b26e-1da520ac9cd6">
<img width="316" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/cb31d47c-4e53-46aa-8fc3-bade7482b230">

### 2.2.3.  Test for Normality
Tests for normality measure whether the dataset has a normal distribution. This means that the distribution of symmetry is centred around the mean, allowing for more accurate results during analysis. I visually checked for normality using histograms. 

### 2.2.4.	Normalization Transformation
To normalize positive skewness, I computed new variables by taking the log of the old variable. For example, Log_CombinedCO2 = ln (CombinedCO2). To normalize negative skewness in “Gears”, I computed a new variable by taking the cubic power of the old variable using this formula: Cubed_Gears = Gears**3. 

<img width="294" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/7d514e1d-85e1-4531-bc06-03ac2e8cbfc6">


# 3.  Data Analytical Methods
## 3.1.  Descriptive Statistics

### 3.1.1.  Mean
The mean measures the average value of data points in the dataset. The average CombinedFE is 23.04 miles per gallon while the average Combined CO2 is ~407grams per kilometre.

### 3.1.2.  Standard Deviation
The standard deviation measures the spread of data points around the mean. These values appear normal and average. 

<img width="365" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/0b3e8b1b-46b3-4e65-9574-93701248aba4">

### 3.1.3.  Pearson's Correlation
Pearson’s coefficient of correlation identifies the nature of relationships between quantitative values, and it assumes a normally distributed dataset (Milovanof, et al., 2019). A coefficient of -1 depicts a perfect negative linear correlation between the variables, a value of 0 means zero correlation, and a value of 1 means a perfect positive linear correlation between the variables. Note that engine displacement refers to the size of the engine.

<img width="406" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/29c0c6c8-ff1d-4706-9ce4-a32ae82dfdfa">

As seen in the Figure above, all correlations are significant at the 0.01 level. There are high negative correlations between independent variables (engine displacement, number of cylinders) and Combined FE. This means that as a vehicle’s engine displacement and cylinders increase, the fuel economy (miles per gallon) decreases. There are also high positive correlations between engine size, number of cylinders and Combined CO2. This means that as engine size and cylinders increase, the car’s CO2 emissions increase as well. There is a high negative correlation between Combined CO2 and Combined FE, meaning that as CO2 emissions increase, fuel economy reduces. 

### 3.1.4.  Linear Regression Analysis

Following the correlation analysis, simple linear regression was used to test if the correlated variables significantly predicted Combined CO2 emissions and Combined FE:

##### H0: There is no significant impact of engine displacement on Combined CO2.
##### H1: There is a significant impact of engine displacement on Combined CO2.

<img width="282" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/b5603f65-ca8e-4ba3-ac37-9ad953106e35">

The fitted regression model1 above is  y = 5.49 + 0.47*x
The overall regression is statistically significant (R2 = 0.756, p = < .001). R2 indicates that 75.6% of the variance in Combined CO2 can be explained by the engine displacement. The fitted model indicates that for every 1 unit increase in engine displacement, Combined CO2 increases by 0.47 units.
Therefore, the null was rejected because engine size (displacement) significantly impacted Combined CO2. 

<img width="268" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/a830a5b3-a485-4614-a66c-fabf9413a271">

##### H0: The number of cylinders does not impact Combined CO2.
##### H2: The number of cylinders significantly impacts Combined CO2.

The fitted regression model2 above is  y = 4.9 + 0.64*x    -------------Figure 18
The overall regression is statistically significant (R2 = 0.715, p = < .001). R2 indicates that 71.5% of the variance in Combined CO2 can be explained by the number of cylinders. The fitted model indicates that for every 1 unit increase in number of cylinders, Combined CO2 increases by 0.64 units. Therefore, the null was rejected because number of cylinders significantly impacted Combined CO2.

<img width="302" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/538c2133-cfde-499b-a12e-aebe42d02572">

##### H0: There is no significant impact of engine displacement on Combined FE
##### H3: There is a significant impact of engine displacement on Combined FE.

The fitted regression model3 above is  y = 34-10.45*x
The overall regression is statistically significant (R2 = 0.712, p = < .001). R2 indicates that 71.2% of the variance in Combined FE can be explained by the engine displacement. The fitted model indicates that for every 1 unit increase in engine displacement, Combined FE reduces by 10.45 units. Therefore, the null was rejected because engine size (displacement) significantly impacted Combined FE.

<img width="278" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/cab98b0c-8b62-4c25-857e-58fde1f4f988">

#####  H0: The number of cylinders does not impact Combined FE.
##### H4: The number of cylinders significantly impacts Combined FE.

The fitted regression model4 above is  y = 47-14.24*x
The overall regression is statistically significant (R2 = 0.661, p = < .001). R2 indicates that 66.1% of the variance in Combined FE can be explained by the number of cylinders. The fitted model indicates that for every 1 unit increase in cylinders, Combined FE reduces by 14.24 units. Therefore, the null was rejected because number of cylinders significantly impacted Combined FE.

### 3.1.5.  Independent Samples t-test
This test was used to determine if the means of Combined FE and Combined CO2 differ significantly among Automatic and Manual cars: 

##### H0: No significant difference in Combined FE among car transmission types.
##### H1: There is a significant difference in Combined FE among car transmission types.

##### H0: No significant difference in Combined CO2 among car transmission types.
##### H2: There is a significant difference in Combined CO2 among car transmission types.

<img width="349" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/b0fd599f-fdce-4185-9d41-a993045a3122">
<img width="464" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/ffa042fa-b370-4311-bea6-2895cf5f0c18">

The Figure above shows that there is a significant difference in the means of Combined FE between automatic cars (1) (Mean = 22.55, SD = 5.079) and manual cars (2) (Mean = 24.85, SD = 5.433). At p = <.001, the results indicate that manual cars exhibit more fuel economy than automatic cars. Therefore, the null hypothesis was rejected.

<img width="372" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/84530efc-158f-498c-90df-51629b179baa">
<img width="451" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/3c57733b-c83b-4ea0-ae02-b21bc187a3ac">

The figure above shows that there is a significant difference in the means of Combined CO2 between automatic cars (1) (Mean = 415.27, SD = 97.51) and manual cars (2) (Mean = 376.46, SD = 90.9). At p = <.001, the results indicate that manual cars produce less Combined CO2 than automatic cars. Therefore, the null hypothesis was rejected.

### 3.1.6. One-Way Anova Test
This test was used to determine if the means of Combined FE and Combined CO2 differed significantly among Turbocharged, Supercharged and Naturally Aspirated cars.

##### H0: No significant difference in Combined FE among air aspiration methods.
##### H1: There is a significant difference in Combined FE among air aspiration methods.

##### H0: No significant difference in Combined CO2 among air aspiration methods.
##### H2: There is a significant difference in Combined CO2 among air aspiration methods.

<img width="266" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/63a79624-8eb7-4aeb-bb71-f8810c95970a">

The figure above demonstrates that there is a significant difference in the means of Combined FE among Naturally transmitted, Turbocharged and Supercharged cars. At Fstatistic  > 1.96 and P <0.05, the results indicate that there is a significant difference between groups of air aspiration methods. The means are 22.69(1), 18.82(2), 24.04(3) thereby confirming that the choice of air aspiration method impacts a car’s fuel economy. Therefore, the null hypothesis was rejected. 

<img width="249" alt="image" src="https://github.com/kelechiu/Statistical_Data_Analysis_Kangaroo/assets/100145388/0fd3f263-f92f-418c-8e81-19b7e92c4c35">

The figure above demonstrates that there is a significant difference in the means of Combined CO2 among Naturally transmitted, Turbocharged and Supercharged cars. At Fstatistic  > 1.96 and P <0.05, the results indicate that there is a significant difference between groups of air aspiration methods. The means are 415.62(1), 479.85(2), 385.5(3) thereby signifying that the choice of air aspiration method impacts a car’s CO2 emissions. Therefore, the null hypothesis was rejected.


# 4.  Evaluation and Conclusion

In conclusion, through a comprehensive statistical analysis of the relationships between different car types, fuel economy and combined CO2, this paper confidently rejects the null hypothesis that:

##### H01: There are no significant differences in fuel economy among different car types. 
##### H02: There are no significant differences in CO2 emissions among different car types.

The first linear regression model highlighted significant causalities between engine displacement, Combined FE and Combined CO2. According to the results, cars with larger engine displacements produce higher CO2 emissions and exhibit lower fuel economy. For every 1 unit increase in engine displacement, Combined CO2 increases by 0.47 units, and Combined FE reduces by 10.45 units.

Additionally, significant relationships were also found between number of cylinders, Combined FE and Combined CO2. The third regression model indicated that cars with higher number of cylinders produce higher CO2 emissions and exhibit lower fuel economy. For every 1 unit increase in number of cylinders, Combined CO2 increases by 0.64 units, and Combined FE reduces by 14.24 units.
The independent samples t-test was conducted to explore the difference in means between Combined FE and Combined CO2 among manual and automatic cars. It found that manual cars produce 9.35% less Combined CO2 than automatic cars. It also concluded that manual cars exhibit approximately 10.2% more fuel economy than automatic cars.

Finally, the One-way Anova test was used to determine if the means of Combined FE and Combined CO2 differed significantly among Turbocharged, Supercharged and Naturally Aspirated cars. It found that the choice of air aspiration method impacts a car’s fuel economy and CO2 emissions.
Although this paper provided valuable insights into the different car types that exhibit more fuel economy and environmental friendliness, it does not consider other factors that could impact the observed trends. Variables like vehicle’s weight, geographic variations and fuel type were omitted from the dataset. As a result, additional research with a robust dataset should be conducted to supplement the findings in this research.


