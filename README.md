# MechaCar Statistical Analysis 👨‍🔧
 Use of Statistics and R
---
## Background

The MechaCar, AutosRUs' newest prototype, is experiencing production issues that are impeding the manufacturing team's progress. Upper management at AutosRUs has asked Jeremy and the data analytics team to review production data for insights that can help the manufacturing team.

In this challenge we will:

* Conduct multiple linear regression analysis to determine which variables in the dataset predict MechaCar prototype mpg.
* Compile summary data on the pounds per square inch (PSI) of suspension coils from manufacturing lots.
* Use t-tests to see if the manufacturing lots differ statistically from the average population.
* Create a statistical study to compare the performance of MechaCar vehicles to other manufacturers' vehicles.

## :one: Deliverable 1

### 1.1 Use the `library()` function to load the `dplyr` and `tidyverse` packages.

#### Code
```
# 1.1 Load packages
library(dplyr)
library(tidyverse)
```

#### Output
![image](https://user-images.githubusercontent.com/98360572/170587149-cc8b18e5-974f-460d-a2c3-477ca617aec0.png)

### 1.2 Import and read in the `MechaCar_mpg.csv` file as a dataframe

#### Code
```
# 1.2 Import and read the csv file MechaCar_mpg.csv
mecha_car <- read.csv(file = 'Data/MechaCar_mpg.csv', check.names = F, stringsAsFactors = F)
head(mecha_car)
```
#### Output

![image](https://user-images.githubusercontent.com/98360572/170586909-4a14a17d-d180-4fb9-9d82-46af3e944483.png)

### 1.3 Perform linear regression using the `lm()` function. In the `lm()` function, pass in all six variables, and add the dataframe created above as the data parameter.

#### Code
```
# 1.3 Linear regression for the six variables using the lm() function
lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD , data = mecha_car)
```

#### Output
![image](https://user-images.githubusercontent.com/98360572/170591748-63d56991-2411-4425-9af4-5944d544ea31.png)

### 1.4 Using the `summary()` function, determine the `p-value` and the `r-squared` value for the linear regression model.

#### Code
```
# 1.4 Use summary to find p-value and r-squared for all variables
summary(lm(mpg ~ vehicle_length + vehicle_weight + spoiler_angle + ground_clearance + AWD , data = mecha_car))
```

#### Output
![image](https://user-images.githubusercontent.com/98360572/170592016-33ee6c36-0557-48bf-8897-1f39f12388a1.png)

## Linear Regression to Predict MPG

* Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset?

In the dataset, it is plausible to anticipate that the following variables and coefficients contributed non-randomly to the mpg value:

`vehicle weight (0.0776)`
`spoiler angle (0.3069)`
`AWD (0.1852)`

RESPUESTA ALTERNATIVA

Variation in weight, spoiler angle, and AWD was not random. Ground clearance and vehicle length were the two factors with the largest random variance.





* Is the slope of the linear model considered to be zero? Why or why not?

P-values (probability values) for the above variables are smaller than our significance level of 0.05, which means they are statistically insignificant. As an example, the significance threshold for vehicle weight is as follows: In other words, 92.2 percent. The intended level of significance is 0.05 - 1 = 0.95 (or 95%). Using data from the linear model, all three variables/coefficients are expected to be outside the 95 percent minimal significance level. Additionally, this model has a statistically significant intersept value (5.08e-08), which suggests additional variables or coefficients that have not been accounted for could contribute to the variation in mpg (nor in the provided dataset). It's possible that more data has to be gathered or observed in order to boost the predictive potential of the analysis. Because the p-value is less than 0.05, the linear model's slope is not assumed to be zero.

RESPUESTA ALTERNATIVA

Our p-value is less than 0.05, so our slope is not zero.





* Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?

According to the summary output, the r-squared value is 0.71, implying that this linear model will correctly predict approximately 71% of all mpg predictions. Furthermore, the linear model's p-value is 5.35e-11 (last line of the above image in the F-statistic results), which is lower (94.65%) than the desired significance level of 0.05. (95 percent ).


RESPUESTA ALTERNATIVA

Our R-squared value is 71 percent, which suggests that around 71 percent of the time the model will properly estimate mpg numbers. The mpg variability of the MechaCar prototypes may be due to other factors that were not included in the data set.




## :two: Deliverable 2

### 2.1 Import and read in the `Suspension_Coil.csv` file as a table

#### Code
```
# 2.1 Import and read the csv file
suspension_coil <- read.csv(file = 'Data/Suspension_Coil.csv', check.names = F, stringsAsFactors = F)
```

#### Output
![image](https://user-images.githubusercontent.com/98360572/170603494-c2052c7a-7c71-4a86-b560-f03fd792cce4.png)


### 2.2 Create a `total_summary` dataframe using the `summarize()` function to get the mean, median, variance, and standard deviation of the suspension coil’s PSI column

#### Code

```
# 2.2 Create total summary df, using summarize()
total_summary <-  suspension_coil %>% summarize(Mean=mean(PSI),Median=median(PSI),Variance=var(PSI),SD=sd(PSI), .groups = 'keep')
```

#### Output
![image](https://user-images.githubusercontent.com/98360572/170603615-f4863252-b09c-4c44-9745-749792e96139.png)

### 2.3 Write an RScript that creates a `lot_summary` dataframe using the `group_by()` and the `summarize()` functions to group each manufacturing lot by the mean, median, variance, and standard deviation of the suspension coil’s PSI column

#### Code

```
# 2.3 Create lot summary df, using group_by() & summarize()
lot_summary <- suspension_coil %>% group_by(Manufacturing_Lot) %>% summarize(Mean=mean(PSI),Median=median(PSI),Variance=var(PSI),SD=sd(PSI), .groups = 'keep')
```

#### Output
![image](https://user-images.githubusercontent.com/98360572/170603948-4b712b62-8b83-43a7-939d-27054d176d95.png)

## Summary Statistics on Suspension Coils

* The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?

![image](https://user-images.githubusercontent.com/98360572/170603711-56b623b9-fca7-4503-bdca-75f54d3daa2e.png)


![image](https://user-images.githubusercontent.com/98360572/170603987-03230624-cab3-4f06-bddb-538def5977ca.png)

The MechaCar suspension coils must not have a deviation of more than 100 pounds per square inch, according to the design specifications. Existing production information meets this design standard for each and every manufacturing lot, individually and collectively? To what end?

There are no significant differences between the mean and median of Lot 1 and Lot 2 based on the design parameters. There is a lot of variation in Lot 3 compared to the manufacturer's specifications.

## :three: Deliverable 3

### 3.1 write an RScript using the `t.test()` function to determine if the PSI across all manufacturing lots is statistically different from the population mean of 1,500 pounds per square inch.

#### Code
```
# 3.1 t-test across all manufacturing lots against the population mean = 1500 PSI
t.test(suspension_coil$PSI, mu=1500)
```
#### Output
![image](https://user-images.githubusercontent.com/98360572/170604850-edbbcb04-34fa-41d4-b327-34d29fe43336.png)

### 3.2 Write three more RScripts using the `t.test()` function and its `subset()` argument to determine if the PSI for each manufacturing lot is statistically different from the population mean of 1,500 pounds per square inch.

#### Code
```
# 3.1.1 t-test lot1 against population mean = 1500 PSI
lot1 <- suspension_coil %>% subset(Manufacturing_Lot=="Lot1")
t.test(lot1$PSI, mu=1500)

# 3.1.2 t-test lot2 against population mean = 1500 PSI
lot2 <- suspension_coil %>% subset(Manufacturing_Lot=="Lot2")
t.test(lot2$PSI, mu=1500)

# 3.1.3 t-test lot3 against population mean = 1500 PSI
lot3 <- suspension_coil %>% subset(Manufacturing_Lot=="Lot3")
t.test(lot3$PSI, mu=1500)
```


#### Output 3.1.1
![image](https://user-images.githubusercontent.com/98360572/170605237-94f442b3-ca78-471e-b5f0-bf65bef9d968.png)

#### Output 3.1.2
![image](https://user-images.githubusercontent.com/98360572/170605319-2b8d9133-1246-4145-90ec-5be27ad4fc0c.png)

#### Output 3.1.3
![image](https://user-images.githubusercontent.com/98360572/170605396-9a794fb7-e5c1-43ee-aefa-e6cc18df85e1.png)

It has been determined through data analysis that the two suspension coil lots with variation and standard deviation less than 100 pounds per square inch will meet the design specifications. Lot 3's variance and standard deviation, on the other hand, are larger than 100 pounds per square inch, so it fails to meet the design criteria.





## T-Tests on Suspension Coils
Using a 93.972 percent confidence interval, we may conclude that the p-value for all lots is less than or equal to 0.06028, which is not statistically significant. There is insufficient evidence to reject the null hypothesis based on this prediction. A statistically equivalent relationship can be found between the dataset's mean and the population's mean. It also appears that the suspension coils dataset is statistically representative of the population mean, according to the results of the investigation.
































