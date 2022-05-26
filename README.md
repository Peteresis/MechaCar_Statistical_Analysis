# MechaCar_Statistical_Analysis
 Use of Statistics and R
---

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













