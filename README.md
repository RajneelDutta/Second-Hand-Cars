# Second-Hand Cars Price prediction

## Introduction

## Dataset

## Preliminary analysis
As an important part of our analysis, we were curious about how the various numerical variables relate to each other. Hence, we plot a Correlation plot. Here is the plot :

![Correlation of Numerical variables](/Plots/Corr-1.png)

The main take-aways from the above plot are these :

• The response variable *Price* is positively correlated with the variable *Cylinders*.

• It is negatively correlated with the variable *Odometer*.

• Year has a very slight correlation with *Price*.

We now start off with looking at how our response variable **Price** is spread.

![Density of Price](/Plots/Price.png)

We notice that prices of the cars are mostly concentrated within the range of $0-$20,000. But we also notice that the distribution is not normal and is right-skewed. Since, prices in general are almost never normally distributed, we can use log-transformation later to use this variable in our models.

Our first independent variable is *Year*. We were curious to see how Year affects the Price of the second-hand cars. This plot reveals some interesting information regarding the same:

![Price vs Year](/Plots/PriceVsYear.png)

We notice that the prices of older cars tend to be higher. This may be due to the added appeal of “vintage” cars.
Since these older cars are much lesser in number, we zoom into more recent cars from around the 1980s.

![Price vs Year (1980)](/Plots/PriceVsYear80.png)

Now this graph points out the following:

• Prices from 1980-2005 stayed mostly the same and did not show any tendencies to increase.

• It started to rise from around 2010, steeply. Some reached even values beyond $60,000.

• Year, thus, has a linear relationship with Price. That is, of course, given if we look at the
recent car prices.

The next variable of interest is *Cylinders*. We are interested to find out if the number of cylinders in a car will affect the price it sells at.

![Price vs Cylinders](/Plots/CylVsPrice.png)

From the above two graphs, we notice a few things such as:

• Maximum number of cylinders is equally spread between 8 and 6, both with 34 cars each. Interestingly, no cars have 7 cylinders.

• There is only 1 car with 10 cylinders. And it has the highest price out of all the others.

• Even though our assumption that prices increase with number of cylinders is true, cars with 4
cylinders enjoy a slightly higher median price than those with 5 cylinders.

We can assume that a log transformation of this variable, down the lane, will be useful for modelling since it is not normally distributed but seems to affect the price of cars.

We generally have an idea that cars that are of the bigger types gets sold at higher prices. Hence, we try to see if the same assumption, that Type of car affects car prices, hold here:

![Price vs Type](/Plots/TypeVsPrice.png)

We notice a few points from the above graphs:

• Sedans have the highest number of cars amongst the others.

• Our assumption holds correct. Bigger car types such as Trucks, Pickups and Vans get sold at
higher prices than the rest.

Lastly, we will look at two more variables that we expect to be big factors in affecting the car prices:
Fuel and Drive.

![Price vs Fuel Type](/Plots/FuelVsPrice.png)

We will keep it short : Diesel cars are more expensive, even though Petrol cars are more in numbers in our dataset.

![Price vs Drive](/Plots/DriveVsPrice.png)

Similarly, Four-Wheel drive cars, on account of them being related to big-sized trucks and SUVs, get sold a higher prices than the other cars.

## Regression Model

We start off by constructing a very basic model, consisting of only the numerical variables year, cylinder, and odometer. We notice that the **AIC value** of this model to be **2187.571**.

Since we have not included the character variables, we create dummy variables of them and construct another model.

The next model is essentially a *Sink model*, containing all the independent variables. The **AIC** comes out to be **2183.824**. Like the Numerical model which had all variables statistically significant under 1%, this Sink model also had only the numerical variables as statistically significant.

We then turn to the Step-wise model. Using this, we arrive at an **AIC** value of **2172.391**. It had the following variables, all statistically significant under 1%: *odometer, cylinders, fuel, and drive.*

So far, the **step model** has given the best AIC value.

We next try to go back and check the histograms of year, cylinder, fuel, odometer, drive, and type and see if they can be transformed to be included in a new model, that builds upon the sink model and give a better one. For this, we also take the help of *Box-Cox transformation*.

After applying BoxCox transformation to the sink model, we arrive at a new model with a better AIC value : *fuel, log(cylinders), odometer, and log(drive)*. This model has an **AIC** value of **2081.008**.

Thus, we have these two best models : Step Model and BoxCox Step Model.
We have chosen the *BoxCox model* as it has the *lowest* AIC values out of all the possible models we tested.

Our aim now is to build upon this model and try to improve it by performing diagnostic analysis on them, which will be handled in a separate project.






