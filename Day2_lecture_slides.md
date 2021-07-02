[Foundations of Data Science with Capstone at SMU, Summer 2021]
Day 2: Visualization (1)
========================================================
author: Dr. Jeho Park
date: 
autosize: true



DAY1 and LAB1 Review
========================================================

Any questions?

Today's Topics
==============


Typical Data Science Project Workflow
===================



Goal of First Few Days
====================
__Learn fun and intuitive ways to learn data using R__

Visualization with ggplot2: tidyverse package
======================
* Load tidyverse package in your environment

```r
# if you don't have the package installed yet
# install.package("tidyverse")
library(tidyverse)
```
>> This should load several packages. See the R message on the console. Notice the "Conflicts" -- what does this mean?

Visualization with ggplot2: a quick look
======================

```r
ggplot(data = mpg) + 
  aes(x = displ, y = hwy, color = class) + 
  geom_point() 
```


```r
# Compare ggplot() with plot() from base package
base::plot(mpg$displ, mpg$hwy)
```

>> Let's look at a grammar of graphics

Visualization with ggplot2: A Grammar of Graphics
=======================

>> A grammar of graphics is a set of tools for building graphics by adding components and transformations __layer by layer__.  

--

>> Every ggplot2 plot has three key components:
>> - __Data__,
>> - A set of __aesthetic mappings__ between variables in the data and visual properties, and
>> - At least one __layer__ which describes how to render each observation. Layers are usually created with a `geom` function.


```r
ggplot(data = mpg) + # data
  aes(x = displ, y = hwy) + # aesthetic mapping
  geom_point() # layer (geometric object)
```

Breakout Session: Guess a relationship between two variables
=======================
1. Look at the help document of the data frame `mpg` (how?)


2. Discuss relationship between any two variables, e.g., engine displacement in liters and highway MPG.

3. See if your guess is in line with the scatter plot


Visualization with ggplot2: A Grammar of Graphics
=======================
Most points on the plot form a nice linear relationship while there are some points that don't seem to follow the relationship. What types of cars are they? 


```r
ggplot(data = mpg) +  
  geom_point(mapping = aes(x = displ, y = hwy), color = class) # create 
```


```r
# Color does not always work for everyone. How about different shapes?
ggplot(data = mpg) +  
  geom_point(mapping = aes(x = displ, y = hwy, shape = class)) # Any issue with the shape option?
```

Faceting by a single variable
=========
__Use `facet_wrap`__

1. the first argument should be a *formula* and  

2. the variable that you pass to `facet_wrap` should be *discrete*.


```r
ggplot(data = mpg) + 
  aes(x = displ, y = hwy) + 
  geom_point() + 
  facet_wrap(~ class, nrow = 2)
# facet_wrap(. ~ class, nrow = 2) # same result
```

>> Question: What is `~`?

What is a R formula?
==================
A formula is an R object containing a symbolic representation of a relationship between variables. Formulas are not For example, **y ~ x + a** is a *formula* which we may read "`y` varies with `x` and `a` (note that the meaning depends on the function in which the formula is used). In most modeling cases, the left-hand side of a tilde (~) is the "dependent variable" (or "response") and the right-hand side is the "independent variable" (or "predictor"). 

Example: In a data frame, you have a variable `t` for temperature and another variable `m` for month. Clearly, month do not vary with temperature, but temperature varies with month. So, you want to see how the temperature varies for different month. How do you write a formula for this model?

What is a discrete variable?
===================
![Variable Types](./images/variable-types.png)

Source: https://statsandr.com/blog/variable-types-and-examples/

What is a discrete variable?
===================

>> Quantitative *discrete* variables are numeric variables for which the values it can take are __countable__ and have a __finite number of possibilities__. The values are usually, but not always, integers. For example:

>> - Number of children per family
>> - Number of students in a class
>> - Number of citizens of a country

Then, what is a continuous variable?
===================
>> Quantitative *continuous* variables are numerical measurements whose values are __not countable__ and have an __infinite number of possibilities__. For example:

>> - Age
>> - Weight
>> - Height

Q: Classify the following variables as continuous or discrete:
===============================================
(1) Temperature in Asan  

(2) The number of sales made in a week  

(3) Time taken to run a 100-meter dash   

(4) The quantity of fat in samgyupsal  

(5) The number of trout in Sinjungho  

LAB2
==================
3.2.4: Do all the problems
3.3.1: Do all the problems
3.5.1: #1


