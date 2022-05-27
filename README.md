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


* Is the slope of the linear model considered to be zero? Why or why not?


* Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?


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

