# Multiple-Linear-Regression-in-R
# Multiple Linear Regression
install.packages("tidyverse")
install.packages("datarium")

library(tidyverse)
library(datarium)
# Loading the dataset

df <- data("marketing", package = "datarium")
View(df)


head(marketing, 4)

# Building the model

# We want to build a model for estimating sales based on the advertising 
# budget invested in youtube, facebook and newspaper, as follow:

# sales = b0 + b1*youtube + b2*facebook + b3*newspaper
#sales = 3.53 + 0.046*youtube + 0.188*facebook
# we remove the newspaper because it is statistically insignificant
# In order to determine how powerful the model we need to observe the adjusted R-squared value(multiple linear) and  R-squared for (simple linear) because R-Squared value increases when explanatory variables are added even if they are weekly associated

model <- lm(sales ~ youtube + facebook + newspaper, data = marketing)
summary(model)
#interaction affect of the independent variables
model1 <- lm(sales ~ youtube * facebook * newspaper, data = marketing)
summary(model1)
