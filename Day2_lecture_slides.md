[Foundations of Data Science with Capstone at SMU, Summer 2021]
Day 2: Visualization (1)
============================
author: Dr. Jeho Park
date: 
autosize: true



Course Site via Canvas
===================

[Online Course Site] <https://canvas.instructure.com/courses/3090373>

- Announcements
- Discussions
- Assignments
- Files
- Quizzes/Surveys 
- Mobile App (App login must use *QR Login*)

__Note: We will not use Google Drive due to some deficiencies as a Learning Management System.__

### Communication Channels
- Canvas: https://canvas.instructure.com/courses/3090373

*Make sure you can log in to the course site NOW*

Daily Survey
=============

- Log in to Canvas from your browser
- Open Assignments
- Open Day1 Survey
- Take the survey (it will  only take a few minutes)

DAY1 and LAB1 Review and Q&A
=========================
- R and RStudio should be installed on your computer
- RStudio's project for the course should be created
- Make sure you have a GitHub account
- Make sure you can render R Markdown (Rmd) file

__Questions__

1. I had a problem downloading the second package,(rmarkdown) from the class, and the error said that I didn't have a lib location. How can I fix this?

2. Why does it always have same three code chunks set as default when I create a new markdown? Is it because I have downloaded a package?

3. I wrote my date as 2021/7/5 on this document but if I knit it it appears as 2016/8/25. What is wrong?


Today's Topics
==============
- Where to get help 
- Grammar of graphics
- Introduction to ggplot2
- Visualization: point geom
- Faceting
- R Fomula
- Discrete Variable

How to Get Help
=====================
* Stack Overflow: http://stackoverflow.com/questions/tagged/r
* Cross-Validated: the statistics Q&A site http://stats.stackexchange.com/
* Google!


[Breakout Session] Where to get help?
=============
- Find Korean websites/community that you can ask questions about R programming (5 min)
- Suggest them in the main room (5 min)


Typical Data Science Project Workflow
===================
![Workflow](./images/data-science.png)


Goal of First Few Days
====================
__Learn fun and intuitive ways to use R for Data Science__

An Example: John Snow's Map
===============
__For informed decision making (data-driven decision making), visualization is much more important than you may think__

<https://www.arcgis.com/apps/PublicInformation/index.html?appid=d7deb67f810d46dfacb80ff80ac224e9>


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
# library(ggplot2)
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
  geom_point(mapping = aes(x = displ, y = hwy, color = class)) # create 
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

>> Question: What is `~` for?

What is a R formula?
==================
A formula is an R object containing a symbolic representation of a relationship between variables. For example, **y ~ x + a** is a *formula* which we may read "`y` varies with `x` and `a` (note that the meaning depends on the function in which the formula is used). In most modeling cases, the left-hand side of a tilde (~) is the "dependent variable" (or "response") and the right-hand side is the "independent variable" (or "predictor"). 

Example: In a data frame, you have a variable `t` for temperature and another variable `m` for month. Clearly, month do not vary with temperature, but temperature varies with month. So, you want to see how the temperature varies for different month. How do you write a formula for this model?

LAB2
==================
- 3.2.4: Do all the problems
- 3.3.1: Do all the problems



