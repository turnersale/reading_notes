# R for Data Science
### Garrett Grolemund, Hadley Wickham <!-- omit in toc -->
### ISBN <!-- omit in toc -->

- [R for Data Science](#r-for-data-science)
- [Preface](#preface)
- [Part 1 - Explore](#part-1---explore)
  - [Chapter 1 - Data Visualization with ggplot2](#chapter-1---data-visualization-with-ggplot2)
  - [Chapter 2 - Workflow: Basics](#chapter-2---workflow-basics)
  - [Chapter 3 - Data Transformation with dplyr](#chapter-3---data-transformation-with-dplyr)
  - [Chapter 4 - Workflow: Scripts](#chapter-4---workflow-scripts)
  - [Chapter 5 - Exploratory Data Analysis](#chapter-5---exploratory-data-analysis)
  - [Chapter 6 - Workflow: Projects](#chapter-6---workflow-projects)
- [Part 2 - Wrangle](#part-2---wrangle)
  - [Chapter 7 - Tibbles with tibble](#chapter-7---tibbles-with-tibble)
  - [Chapter 8 - Data Import with readr](#chapter-8---data-import-with-readr)
  - [Chapter 9 - Tidy Data with tidyr](#chapter-9---tidy-data-with-tidyr)
  - [Chapter 10 - Relational Data with dplyr](#chapter-10---relational-data-with-dplyr)
  - [Chapter 11 - Strings with stringr](#chapter-11---strings-with-stringr)
  - [Chapter 12 – Factors with forcats](#chapter-12--factors-with-forcats)
  - [Chapter 13 - Dates and Times with lubridate](#chapter-13---dates-and-times-with-lubridate)
- [Part 3 - Program](#part-3---program)
  - [Chapter 14 - Pipes with magrittr](#chapter-14---pipes-with-magrittr)
  - [Chapter 15 - Functions](#chapter-15---functions)
  - [Chapter 16 - Vectors](#chapter-16---vectors)
  - [Chapter 17 - Iteration with purr](#chapter-17---iteration-with-purr)
- [Part 4 - Model](#part-4---model)
  - [Chapter 18 - Model Basics with modelr](#chapter-18---model-basics-with-modelr)
  - [Chapter 19 - Model Building](#chapter-19---model-building)
  - [Chapter 20 - Many Models with purr and broom](#chapter-20---many-models-with-purr-and-broom)
- [Part 5 - Communicate](#part-5---communicate)
  - [Chapter 21 - R Markdown](#chapter-21---r-markdown)
  - [Chapter 22 - Graphics for Communication with ggplot2](#chapter-22---graphics-for-communication-with-ggplot2)
  - [Chapter 23 - R Markdown Formats](#chapter-23---r-markdown-formats)
  - [Chapter 24 - R Markdown Workflow](#chapter-24---r-markdown-workflow)

# Preface
- Install: R, RStudio, the Tidyverse package, nycflights13, gapminder, lahman packages
- >: the prompt will appear before any code block (the book doesn't include the prompt in the examples)
- #>: notation that the book uses to comment out the output of the code
- The book has certain conventions:
  - Functions use a set font and followed by parentheses
  - Other objects will also be in code font
  - If specifying the package from which an object comes from, it will be followed by two colons and the package name (which is valid R code in itself)
- If you need help, the best resources tend to be Google and Stackoverflow
- If an answer does not exist, you can make a reprex by:
  - Including packages at the top of the script
  - Include data from the smallest subset that shows the error
  - Spend some time making sure others can read your code easily

# Part 1 - Explore

- The goal is to generate many possible, promising leads to then investigate further
- The primary order when doing data science with R is the following:
  - Import the data
  - Tidy the data
  - Explore
    - Transform, visualize, model, repeat
  - Communicate
- Modeling is an important part of the exploratory process, but we will return to it later when we have better tools to handle it

## Chapter 1 - Data Visualization with ggplot2

- _ggplot_: one of many ways to build visualization, but as one of the most supported, it is best to begin and become proficient with it in order to apply it in many ways
- In order to retrieve the necessary members of the _tidyverse_ that we will use, run:
  - _library(tidyverse)_
  - If this does not work, then you must install it first by running:
    - _install.packages('tidyverse')_
- Installation of packages only needs to happen once, but you need to load it in every new instance that you want to use it in
- For the first example, we need to load a data frame in _ggplot2_ called _mpg_ by calling it in the R code
- In order to learn more about an element you can visit its help page by adding ? before it
- To create a simple plot you can run:
``` r
ggplot(data = mpg) +
geom_point(mapping = aes(x = displ, y = hwy))
```
- _ggplot()_:creates a plot without any layers, and thus is essentially empty
- _geom_point()_: adds a layer of points, one of many geom functions, which all take mapping arguments
  - Requires _aes()_ and its arguments in order to tell the plot how to relate the data
- _aes()_: defines the aesthetics mapping for the plot
- The generic template for creating a graph with _ggplot_:
``` r
ggplot(data = data) +
geom_function(mapping = aes(mappings))
```
- Return to pg. 6 for exercises
- Aesthetic mappings:
  - Aesthetic: visual property of the objects in your plot
    - Can alter size, shape, or color of your plot
  - You can add a third variable to the example plot such as class in this manner
  - Inside of the aes() you can add:
    - _, color = class_
  - _ggplot2_ will automatically assign a unique level of the aesthetic (in this case color) to each unique value of the variable, a process known as scaling
  - Other aesthetics include: size, alpha (transparency), or shape
- You can also alter some of the aesthetics of the graph outside of _aes()_, such as change the color of all the points with:
  - ``` color = 'blue' ```
- Page 12 has a diagram of all the default R point types and their corresponding number code
- Page 12 for exercises
- You can get help with any function using a ? prior to the function call, or by pressing F1 in RStudio
- Facets:
  - One way to add variables is with aesthetics, another is with facets
  - A facet splits your plot into subplots that each display one subset of the data (useful for categorical variables)
  - _facet_wrap()_: facet a plot by a single variable
    - First argument is a formula, started with ~ then followed by a variable name (formula meaning data structure in R, not equation)
    - Second argument is the number or rows in which you want the facet to output
  - _facet_grid()_: facet a plot on the combination of 2 variables
    - First and only argument is a formula containing the first variable, then tilde, then the second variable
  - If you don't want to facet in the rows or columns dimensions, you can use a . instead of a variable name
    - E.g. ``` + facet_grid(.~cyl) ```
    - If the _.~_ falls before the data structure, then the facets will be columnar
    - If the _~._ Comes after the data structure, then the facets will be on rows
- Exercises on pg. 15
- Geometric objects:
  - Plots can use different plotting methods to display data, for example, you can use a barchart geom, a point geom, or a line geom
  - This can be done by altering the geom type:
    - E.g. geom_point for scatterplot vs. geom_smooth for the smooth geom
  - Some aesthetics may not work with certain geoms (for example, a line cannot have a different shape like a point geom can)
  - You can even place multiple geoms on the same graph!
  - ggplot2 has over 30 different geoms and they can each be found on the ggplot2 cheat sheet online
  - If you want to use multiple geoms, it is best to pass your set of mappings to _ggplot_ itself, this will tell it to accept the variables as the global mappings and thus future calls will use the same ones (this way you don't have to alter 2 or more sets of mappings in order to change one variable)
  - You can pass new mapping into the individual geom functions to be treated as local mappings (which allows different aesthetics in different layers)
- Exercises on pg. 20
  - _se =_ : standard error computation, if true then it will calculate
  - _show.legend =_ : true will display the legend next to the plot
- Statistical Transformations:
  - Some graphs plot only the raw data whereas other graphs (like bar graphs) will perform calculations to generate new values to plot
  - _Stat_: The algorithm used to calculate the new values for a graph
  - You can often used the stat used for a certain geom in place of the geom itself
    - E.g. you can replace a bar graph with the _stat_count()_ function
  - There are three reasons you may need the stat instead of the geom itself
    - You want to overwrite the default stat for a geom (an example could be creating a bar chart, but the height of the bar is defined in your dataset, thus it would only have a count of 1, so you can then overwrite it to show the identity stat instead of count)
    - You may want to overwrite the default in order to show the mapping of transformed variables as aesthetics (such as a column that shows the probability, stat_count would show the count, but if you map it to an aesthetic you can get the probability)
    - You may want to draw attention to the statistical transformation you are using in your code
- Exercises on pg. 26
  - _stat_summary_: version of _stat_bin_ that is more flexible, it essentially can perform any aggregation, not just count
  - _geom_bar_ vs. _geom_col_: bar used the stat_count while col used stat_identity, this means that by default, bar will calculate the count from the data, whereas col will use the original data to get its height
  - _stat_smooth()_ is effectively an alias for _geom_smooth()_
- Position Adjustments:
  - Another useful aesthetic with bar charts is that of fill
    - Will automatically color stack each bar
      - E.g. if the bars show count of a certain cut of diamond, you can use fill to color the proportion of each bar based on the clarity
  - This demonstrates the position adjustment ability
  - There are three types of position:
    - _identity_: will place each object exactly where it falls in the context of the graph, not all that useful for bar graphs unless you make the graph itself fairly transparent
    - _fill_: works like stacking from the previous point, but it makes all the bars the same height, coloring each bar as a proportion of the same total (1) rather than by the count
    - _dodge_: places overlapping objects beside each other rather than stacking them, thus showing multiple bars inside of one larger 'bar group'
    - _jitter_: adds a certain level of random noise to each point to avoid gridding
      - Gridding: if point being plotted are the same value or rounded to the same value, only one point will appear, even if 2+ of the same point should be displayed. By jittering, all the point will be displayed as no 2 will be exactly the same value
      - Because this jitter function is so useful in making your graph more revealing, ggplot2 actually has a geom that corresponds to ``` geom_point(position = 'jitter') ```, namely _geom_jitter_
- Exercises on pg. 31
  - _width = ''_ : used in _geom_jitter()_ to determine the amount of vertical and horizontal jitter
    - The jitter is both positive and negative, so the number is doubled to determine the spread
    - The default is 40% of the resolution of the data
- Coordinate Systems:
  - Default is the Cartesian coordinate system where x and y position act independently to find the location of each point
  - _coord_flip()_: switches the x and y axes. Can be useful for things like horizontal boxplots or extra long labels that do not fit well in a normal graph
  - _coord_quickmap()_: sets the aspect ratio correctly for maps. Useful for plotting spatial data.
  - _coord_polar()_: polar coordinates. Reveal an interesting connection between a box chart and a Coxcomb chart (plot in RStudio to see the difference)
- Exercises on pg. 33
  - _labs()_ : used to modify the axis, legend, and plot labels
  - _coord_map()_ vs. _coord_quickmap()_ : maps a projection of a portion of the Earth's surface onto a 2d plane, which does not typically preserve straight lines vs. quickmap which uses a quicker approximation that does preserve straight lines
  - _geom_abline()_ : creates reference lines in the plot (horizontal, vertical, or diagonal)
- Layered Grammar of Graphics:
  - With the new features, we can now use a more complete graphic template
``` r
ggplot(data= data) +
geom_function(
mapping = aes(mappings),
stat = stat,
position = position
) +
coordinate_function +
facet_function
```

## Chapter 2 - Workflow: Basics

- Assignment statements: all R statements where you create objects, all have the same form:
  - _object_name <- value_
  - Can be read as 'object name gets value'
  - It can be a pain to write this over and over so you can use the default shortcut of (Alt-).
- Object names must start with a letter, and can only contain letters, numbers, (_), and (.).
- There are several different naming conventions that people use
  - snake_case
  - CamelCase
  - using.periods
  - andNothing.thatHasaRhym.or.reason
- RStudio uses autocompletion similar to Intellisense in VS IDE's
- R will do all the tedious computation for you, but you must be completely precise in your instructions
- _seq()_ : creates a sequence of numbers starting with the first argument and ending with the second argument
- If you do not pair a parenthesis or quotation mark with another, then R will return to you the continuation character (+)
- If you want to assign a value and then immediately view it, you can surround it with parentheses to automatically print to screen after assignment
- Exercises on pg. 40
  - Alt+Shift+K: opens the keyboard shortcut quick reference

## Chapter 3 - Data Transformation with dplyr

- Rarely will you receive data in the exact manner that you would like, and thus you may need to transform it to get it in the format or order you want
- We will use the dplyr package from the tidyverse for this task
- dplyr does overwrite some of the functions in base R
- When viewing the data frame, you may notice that the rows and columns are limited by the viewport, and thus will tell you how many additional rows are in the dataset, as well as give a list of the column names and the type of each variable
  - int = integers
  - dbl = doubles, or real numbers
  - chr = character vectors, or strings
  - dttm = date times (a date and a time)
  - lgl = logical, vectors that only contain TRUE or FALSE
  - fctr = factors, R uses them to represent categorical variables with fixed possible values
  - date = dates
- 5 key dplyr basic functions:
  - _filter()_ :
  - _arrange()_ :
  - _select()_ :
  - _mutate()_ :
  - _rize()_ :
- _filter()_ :
  - Allows you to subset observations based on their values
  - First argument is the name of the data frame
  - Second and subsequent arguments are the expressions that filter the data frame
  - R provides many common comparison operators like >, >=, <, <=, !=, and ==
- All of the above 5 functions can be combined with _group_by()_, which changes the scope of each function from operating on the entire dataset to operating on it group-by-group
- dplyr functions never modify the input, if you wish to save the output you must assign it to a variable
- _near()_ :
  - Computers use finite arithmetic, so when evaluating a floating point number you should use this approximation operator
  - Used to surround the function that you are evaluating
- _x %in% y_ :
  - Selects every row where x is one of the values in y
  - E.g. month %in% (11|12) would evaluate for any rows where the month is November or December
- De Morgan's law:
  - !(x &amp; y) is the same as !x | !y, and !(x | y) is the same as !x &amp; !y
- _is.na()_ : to determine if a value is missing
- Exercises on pg. 49
  - _between()_ : used to find numerical values between two bounds (inclusive)
- _arrange()_ :
  - Works similarly to filter() except that instead of selecting rows, it changes their order
  - If you provide more than one column name, each additional column will be used to break ties in the values of preceding columns
  - _desc()_ : reorders the column in a descending order
  - Missing values are always sorted at the end
- _select()_ :
  - Allows for the selection of a subset of the dataset (must like a select statement in SQL)
  - Can specify variables with a comma separated list
  - If you use a colon between two variables then it will include all variables between them (inclusive)
  - If you place a minus sign (-) and enclose the variables in parentheses, R will select everything other than the specified variables
  - There are some helper functions that you can use within the select function
    - _starts_with(<characters>)_: matches names that begin with <characters>
    - _ends_with(<characters>)_
    - _contains(<characters>)_
    - _matches(<expression>)_ : matches based on a regular expression, which will be elaborated upon in Ch. 11
    - _num_range(<x>, <#>:<#>)_: matches x1, x2, … xn
  - Select can be used to rename variables, but it will ignore any variable not explicitly mentioned, thus you should use rename()
  - _rename(<dataset>, <new_name> = <old_name>)_ remaps a new name to an existing variables and leaves the remainder unaltered
  - _everything()_: can be used in conjunction with select, often used after the specifying certain variables that you wish to put before the others
    - E.g. if you wish to put color and product type ahead of all other columns (like size, weight, description, etc.) the you would use:
      - select(products, color, product_type, everything())
  - Selecting a variable more than once will only display it one time
  - _one_of()_: evaluates if a variable name happens to fall within a character vector (a set of characters)
  - Select helpers default to being case insensitive, if you wish to make them case sensitive you must alter it by including the second argument _ignore.case = FALSE_
- _mutate()_ :
  - Adds new columns to the end of the dataset (by default) that are functions of existing columns (like a calculated column in DAX)
  - You can reference a column that you are creating inside the same mutate() call, as long as the called variables precedes the reference
  - _transmute()_ : if you only wish to keep the new variables in your new dataset
  - All functions used within mutate() must be vectorized, meaning they take a vector as an input and output a new vector with the same number of outputs
  - Useful/common functions that are paired with mutate()
    - Arithmetic operators:
      - _+,-,/,^_
      - All of these are vectorized
      - 'Recycling rules' apply
      - Meaning they will automatically extend one parameter if it is shorter than another within the same function, i.e. it will give them the same granularity
      - Also useful in conjunction with the aggregate functions like sum() and mean()
    - Modular arithmetic:
      - %/% : integer division
        - Returns the number of times the second parameter can fit inside the first parameter, and will always be an integer that ignores remainders and decimals
        - E.g. 550 %/% 100 returns 5
      - %% : remainder
        - Returns the remainder after an integer division, with the second parameter being the number by which you are dividing the first parameter
        - E.g. 550 %% 100 returns 50
    - Logs:
      - _log(), log2(), log10()_
      - Useful for transformation over data that has ranges over multiple orders of magnitude
      - Also convert multiplicative relationships to additive, which will be covered more in depth in Part 4
      - All else being equal, log2() is often the easiest to use, as a difference of 1 on the scale is equivalent to doubling and -1 to halving
    - Offsets:
      - _lead()_ and _lag()_ : used to reference either leading or lagging variables (the variable before or after)
      - Most useful when combined with a group_by()
    - Cumulative and rolling aggregates:
      - R comes standard with certain running sums, products, mins, and maxes, namely: _cumsum(), cumprod(), cummin(), cummax()_
      - dplyr also provides _cummean()_ for cumulative means
      - If you need rolling aggregates then the R package RcppRoll can be used
    - Logical comparisons:
      - _<, <=, >, >=, !=_
      - If creating a complex sequence of logical operators it is often best to store the interim values as new variables so you can check each step for correctness
    - Ranking:
      - _min_rank()_ : defaults to giving the smallest values the smallest ranks, use desc(x) to give the largest values the smallest rank
      - Many other ranking, but min_rank() is the most common and accomplishes most tasks
      - Some other variants:
        - _row_number(), dense_rank(), percent_rank(), cume_dist(), ntile()_
        - Check help pages for more information if you need them
- Exercises on pg. 58
  - In order to handle ties in the ranking functions, you can use _ties.method()_ on a vector of column names to establish the order by which you want to break ties
  - Trigonometric functions:
    - _sin(), cos(), tan(), acos(), asin(), atan(), atan2( y, x), cospi(), sinpi(), tanpi()_
      - _a-_ the arc- of a function
- Grouped Summaries with summarize():
  - _summarize()_ : collapses a data frame to a single row
    - Not terribly useful unless using it with a group_by()
      - This will group rows based on the group_by() then compute the summary by each group, rather than on the entire dataset (which may not give you the information you need)
- Combining Multiple Operations with the Pipe:
  - _%>%_ : the pipe
    - Improves readability of code
    - E.g. x %>% f(y) %>% g(z) would be the same as g(f(x, y), z)
  - _na.rm_ : argument used in many aggregators to remove the missing values prior to computation
    - If = TRUE then it will remove the missing values
    - You can also filter out the missing values prior to computation using filters like _!is.na()_
- Counts:
  - Important to include either a count(), or a count of non-missing values {like sum(!is.na(x)) } in order to determine if you are drawing conclusions with small amounts of data
  - _as_tibble(<package>::<dataset>)_ :
    - Converts the dataset into a tibble to make printing easier
  - Important to remember that the variance decreases as more data points are added. So if you see outliers you may need to include a filter to remove them if they are truly outliers.
- Useful Summary Functions:
  - Measures of location: useful to combine aggregation with logical subsetting (will be discussed in further detail on pg. 304)
  - Measures of spread:
    - _sd(x)_ : the standard deviation, mean squared deviation
    - _IQR(x)_ : the interquartile range
    - _mad(x)_ : median absolute deviation
    - mad(x) and IQR(x) are more robust version of sd(x) that can be useful when the dataset contains many outliers
  - Measures of rank:
    - _min(x), max(x)_ : rank the smallest or largest
    - _quantile(x, <n>)_ : quantile, will find the value that equals (<n>) < x < (1-<n>)
  - Measures of position:
    - _first(x), last(x)_ : the first or last data point based on position in dataset
    - _nth(x, <n>)_ : returns the <n>th data point from a set
  - Counts:
    - _n_distinct(x)_ : counts the number of unique values
    - _count()_ :
      - Provided by dplyr to give count if that is all you want
      - Can also be used with a weight variable to 'count' the variable (something like a sum)
        - E.g. count(tailnum, wt = distance) would give you the number of miles that the specific plane has travelled in total
  - Counts and proportions of logical values:
    - When used in numeric functions, TRUE is converted to 1 and FALSE to 0, thus sum() and mean() can be very useful (sum() for giving the number of TRUEs and mean() for the proportion of TRUE/FALSE)
- Grouping by Multiple Variables:
  - When grouping by multiple variables, each summary 'peels off' one level of grouping, making it easy to progressively roll up a dataset
    - E.g.

Daily <- group_by(flights, year, month, day)

(per_day <- summarize(daily, flights = n()))

#> output

(per_month <- summarize(per_day, flights = sum(flights)))

#> output

(per_year <- summarize(per_month, flights = sum(flights)))

    - Need to be careful when doing this, sums and counts work well, but you need to think about weighting means and variances. It's also not really possible to roll up rank based statistics like the median
- Ungrouping:
  - _ungroup()_ : used to remove the grouping before performing new calculations on the ungrouped dataset
- Exercises on pg. 72
  - Combining mutate() and the pipe %>% can add columns into the dataset you are using, which can then be referenced in later code blocks
  - Passign the _sort_ argument to count() sorts the results in order of n. This can be used whenever you would use count() followed by arrange()
- Grouped Mutates and Filters
  - Grouping is most useful when used with summarise(), but you can also do convenient operations with mutate() and filter()
  - Generall grouped filters (a grouped mutate followed by an ungrouped filter) are avoided except for very quick and dirty manipulations
  - Functions that work best in grouped mutates and filters are know as window functions
    - Can learn more about them in _vignette('window-functions')_
- Exercises on pg. 75

## Chapter 4 - Workflow: Scripts

- Ctrl+Enter will run the current expression and moves the cursor to the next expression
- It is best to include the libraries in the beginning of your code, but DO NOT include install.packages() as it will alter the other person's computer and that is a big no-no
- Ctrl+Shift+S runs the whole script

## Chapter 5 - Exploratory Data Analysis

- Also abbreviated EDA
- Iterative cycle:
  - Generate questions about your data
  - Search for answers by visualizing, transforming and modeling your data
  - Use what you learn to refine your questions and/or generate new questions
- Two loose example questions can be written as:
  - What type of variation occurs within my variables?
  - What type of covariation occurs between my variables?
- Some basic term definitions:
  - Variable: a quality, quantity, or property that you can measure
  - Value: the state of the variable when you measure it
  - Observation/ case: a set of measurements made under similar conditions (sometimes refered to as a data point, even though it will likely contain multiple variables and values)
  - Tabular data: set of values, each associated with a variable and an observation
- Variation: the tendency of values to change from measurement to measurement
- Visualizing Distributions:
  - How you visualize will depend on whether the variable is continuous or categorical
  - Categorical are most frequently visualized as bar charts
  - Continuous variables are typically shown in histograms
  - In a histogram you can later the bin values (left and right bounds) by altering the _binwidth_ value
  - If you wish to stack histograms it is best to use _geom_freqpoly()_ as it will use lines instead of bars
  - Good questions to ask when you make these graphs:
    - Which values are common? Why?
    - Which are rare? Why? Is this expected?
    - Are there any strange patterns?
    - Why are there clusters?
    - What would cause such clustering?
    - Why might clusters be misleading?
- Unusual Values:
  - Outliers:
    - Data points that don't seem to fit the pattern
    - May be an error in data entry, important new science, or unusual values
    - Can zoom in on graphs with outliers by using the _coord_cartesian()_ function
    - _coord_cartesian(ylim(<min>,<max>), xlim(<min>,<max>))_
  - Missing values:
    - Two options if you have unusual data points in the set
      - Drop the entire row with strange values
        - Not recommended as you may end up removing all your rows due to bad data or poor collection methodologies
      - Replace the unusual values with missing values
        - Can do this easily with mutate( <variable> = ifelse())
        - _ifelse(<argument_test>, <value_if_TRUE>, <value_if_FALSE)_
    - ggplot will allow you to use NA points, and it will not graph them, but it will tell you that there are NA points
      - You can suppress this warning by setting na.rm = TRUE
- Exercises on pg. 93
- Covariation: the behavior between variables. Easiest way to see this is to plot the variables
- A Categorical and Continuous Variable:
  - The best method for graphing the distribution of a continuous variable broken down by a categorical variable is a boxplot
  - Boxplot:
    - Box stretches from the 25th percentile (quartile 1) to the 75th percentile (q3), also called the interquartile range (IQR)
    - Visual points that fall 1.5xIQR from the edges of the box (below or above) are classified as outliers
    - A whisker that extends from the edge of the box to the last number that is not an outlier
  - _reorder(<variable>, <order>, FUN = median)_ : reorder the categorical variable based on another variables or argument
  - _coord_flip()_ : flips the graph by 90 degrees

- Exercises on pg. 99
  - _ggstance_ is a package that allows for the creation of horizontal versions of the ggplot plots. They are the named the same except for an added _h_ at the end of the function
    - E.g. geom_barh()
  - _lvplot_ is a package that allows for the use of letter plots
    - _geom_lv()_ will use the letter plot (similar to boxplot but more accurate and informative for large data sets above 1000 samples or so, splits into segments based on percentile ranges )
  - _geom_violin()_ : similor to a letter plot, but will smooth edges to show continuous variables rather than lettered segments
  - You can facet a histogram of continuous data with a discrete variable as your faceting argument to get multiple graphs and view the data more easily
  - _ggbeeswarm_ is a package used for reducing the data loss in visualization normally seen due to overplotting (one point on top of another) similar to geom_jitter()
    - Adds:
      - _geom_quasirandom()_ : uses van der Corput sequence or Tukey texturing to space dots to avoid overplotting
      - _geom_beeswarm()_ : uses the beeswarm library to do point_size offset
      - Can handle categorical variables on the y-axis
      - Automatically dodges if a grouping variable is categorical and dodge.width is specified
- Two Categorical Variables:
  - Can use _geom_count()_ with a mapping of two variables, which will display circles whose sizes indicate the number of observations that occurred at each combination of values
  - Can also use the count() feature in dplyr then use _geom_tile()_ and the fill aesthetic
    - E.g. diamonds %>%

count(color, cut) %>%

ggplot(mapping = aes(x = color, y = cut)) +

geom_tile(mapping = aes(fill = n))

    - Creates a nice 'picture' with color gradient indicating the number of occurrences
  - If the categorical variables are unordered, you may want to use the _seriation_ package to order them then look for patterns
  - Larger plots may be done with _d3heatmap_ or _heatmaply_ packages that allow for the creation of interactive plots
- Exercises on pg. 101
- Two Continuous Variables:
  - Simplest way is to use a scatter plot
  - As the data gets larger this becomes harder
  - _hexbin_ package includes _geom_hex()_
  - _geom_bin2d()_ : divides the coordinate plane into 2d bins then uses them with a fill color to display the number of points that fall into each bins
  - _geom_hex()_ : similar to geom_bin2d() but instead of boxes it creates hexagons
  - You could also bin one variable as if it was continuous and use some of the techniques described above
    - If using a graph like a boxplot it may be useful to include a way to look at the number of observation inside each boxplot, thus you can use _varwidth = TRUE_, this will create the multiple boxplots as normal (one for each bin) but will adjust the width of each bin to represent the proportion of data that is contains compared to the other boxplots)
- Exercises on pg. 104
  - _cut_number()_ : divides the continuous number into bins with the same number of observations based on how many bins you want
    - _cut_number(<variable>, <number_of_bins>)_
  - _cut_width()_ : divides a continuous variable into bins based on a defined width
    - E.g. you want all bins to have a range of $5000, so they would go 0-5000, 5001-10000, 10001-15000
- Patterns and Models:
  - If you spot a pattern:
    - Could this be coincidence?
    - How could I describe the relationship implied by the pattern?
    - How strong is the correlation that is implied?
    - What other variables may affect the relationship?
    - Does this relationship change if you look at subgroups?
  - _modelr_ package has some useful tools for calculating things like residuals and will be covered later
- Learning more:
  - ggplot2 book from ggplot2.org, usually can get for free if in university at SpringerLink
  - R Graphics Cookbook by Winston Chang
  - Graphical Data Analysis with R by Antony Unwin

## Chapter 6 - Workflow: Projects

- What is Real?
  - Best to consider your R scripts as real, as you can return to them without having to recreate every line and function
  - Removed RStudio's autosave feature
  - Ctrl+Shift+F10 will restart RStudio
  - Ctrl+Shift+S will rerun the current script
- Where does you Analysis Live?
  - R saves files into, and pulls them out from, your working directory, which can be at the top of the console under files, or viewed using: _getwd()_
  - You can also set the wd from within R, but it is not recommended
- Paths and Directories:
  - Two basic types: Mac/Linux and Windows
    - Mac/Linux separate components with slashes (/) while Windows uses backslashes (\)
      - Because \ is special in R syntax, you actually need to type two \'s together to get one in the code (\\), thus it is easier to use the Mac/Linux style
    - Absolute paths:
      - In Windows they are headed by a letter drive like C: or by two backslashes like \\server
      - In Mac/Linux always start with a slash /user
      - DO NOT use absolute paths, no one else will be able to run your code if not on your machine
    - ~ : points to your home directory, Windows doesn't recognize this, so it points you to the documents folder
- RStudio Projects:
  - Common practice is to store all data, inputs, scripts, outputs, etc. in a project folder so as to keep all data together
  - Creation of a new project allows you to choose where to store the project and the name
  - If you always save files with R code rather than the mouse or clipboard you will be able to reproduce work more easily, as everything will be stored properly

#

# Part 2 - Wrangle

- Three main parts: Import, Tidy, Transform
- Chapter 7 focuses on the tibble
- Chapter 8 discusses how to pull from the disk into R, focused on plain-text rectangular format with tips for other types of data
- Chapter 9 is about tidy data
- Chapter 10 gives tools for working with multiple inter-related datsets
- Chapter 11 introduces regular expressions for manipulating strings
- Chapter 12 shows how R stores categorical data
- Chapter 13 focuses on dates and date-times

## Chapter 7 - Tibbles with tibble

- _tibble_ package helps to overwrite some of base R to perform better in the modern world, comes packed in tidyverse
- _data.frame_ will be used to differentiate tibbles from data frames when necessary, otherwise they are interchangeable
- Creating Tibbles:
  - _as_tible()_ : converts a standard data frame into a tibble
  - _tibble()_ : creates a tibble from individual vectors
    - E.g. tibble(x = 1:5, y = 1, z = x ^2 + y)
    - It's possible to assign non-syntactic names to R that are not normally valid names, but you need to surround them with backticks
      - E.g. `:)` = 'smile'
    - Backticks are also needed in other packages like ggplot2 and dplyr
    - _tribble()_ : short for transposed tibble, often used for data entry inside of the code
      - E.g. tribble(

~x, ~y, ~z,

#--/--/----

'A', 2, 3.6,

'B', 1, 8.5

)

      - Many people use the comment line to show where the headers are compared to the data
- Tibbles Versus data.frame:
  - Two main differences:
    - Printing:
      - Tibbles show only the first 10 rows and the columns that fit in the viewing window only, as well as showing the column type
        - You can alter the output using _print()_
        - _print(n = <number_of_rows>, width = <width>)_
        - _width = Inf_ will show all columns
    - Subsetting:
      - _$_ : extracts by name
      - _[]_ : extracts by name or position
      - Can see these behaviors on pg. 123
- Interacting with Older Code:
  - If you run into a piece of code that cannot operate on a tibble, you can use _as.data.frame()_ to convert a tibble back into a data frame
  - [ is the main reason that older code may not work with tibbles, but it has become less common and is not used very often in this book
  - _tibble::enframe()_ : converts named vectors to a data frame with the names and values as separate columns

## Chapter 8 - Data Import with readr

- readr is part of the tidyverse package
- Most readr functions are concerned with turning flat files into data frames:
  - _read_csv()_ : reads comma-delimited files
  - _read_csv2()_ : reads semicolon-separated files (more common in countries where the , is used as the decimal point)
  - _read_tsv()_ : reads tab-delimited files
  - _read_delim()_ : reads files with any type of specified delimiter
  - _read_fwf()_ : reads fixed-width files, specifying fields either by width (_fwf_widths()_), or by position (_fwf_positions()_)
  - _read_table()_ : reads a common variation of fixed-width files where columns are separated by whitespace
  - _read_log()_ : reads Apache style log files
    - _webreadr_ package is built on this function but provides many more tools
- We will focus on read_csv() as most functions have similar syntax and CSV is very common
- _read_csv_ :
  - First argument is the path to the file to read
  - Once read_csv() is run it will first print out a column specification detailing the columns and the types
  - You can also supply an inline CSV file (rows separated by line and columns by commas)
  - You can use another argument to either skip lines or use a certain character to comment out lines
    - s_kip = <n>_ : will skip the first n lines from the input
    - _comment = '<character>'_ : any line that starts with the character will be commented out
  - If the data doesn't have column names you can use _col_names = FALSE_ to tell it not to treat the first row as headers, and instead label them X1, X2…, Xn
    - col_names can also take a vector that R will then use as the column names
      - E.g. col_names = c('x', 'y', 'z')
  - _na =_ : used to define which character represents NA values in your imported file
- Compared to Base R
  - readr functions tend to be much faster (around 10x)
  - They produce tibbles, and don't convert character vectors to factors
  - More readily reproducible
- Exercises on pg. 128
  - read_csv() and read_tsv() share all the same arguments as they are specified forms of the generic read_delim()
  - The most important argument for fwf_widths() is _col_positions_, as this tells the function where the data columns begin and end
  - If you are passing a value that contains a comma inside of it, read_csv() will default to using ' to read the text as a value and not additional columns
  - _\n_ : used to tell read functions when to start a new row
- Parsing a Vector
  - _parse_\*()_ functions take a character vector and return a more specialized vector, such as logical, integer or date
  - Uniform much like the read_\*() functions
    - First argument is the character vector to parse
    - na argument specifies which string should be treated as missing
  - If parsing fails, you will get an error warning
    - The subsequent output will be missing the values that appear in the error warning
  - You can use _problems(<x>)_ to retrieve all the errors from the set
  - The 8 most important parsers:
    - _parse_logical()_
    - _parse_integer()_
    - _parse_double()_
    - _parse_number()_
    - _parse_character()_
    - _parse_factor()_
    - _parse_datetime()_
    - _parse_date()_ and _parse_time()_ (included as one)
  - Numbers:
    - Three problems:
      - People write differently (for example, usign the comma as the decimal separator)
      - Numbers are often surrounded by other charaters like % or $
      - Often have grouping characters that may differe across the world, such as '1,000,000'
    - In order to compensate for the difference in decimal marks, you can create a new 'locale' in the parse function and assign the mark you choose (a period is te default) solving the first problem
      - E.g. parse_double('1,23', locale = locale(decimal_mark = ','))
    - parse_number() ignores any characters before or after the numbers, eliminating hte second problem
    - In order to solve the third problem and remove grouping marks, you can combine parse_number() with locale to remove them
      - E.g. parse_number('$123.456.789', locale = locale(grouping_mark = '.')) #> 123e+08
  - Strings:
    - Converting from character to character may not be as easy as it seems
    - In R you can see the underlying hexadecimal number by using _charToRaw()_ which will output the hexadecimal number for each character in the string
    - Hexadecimals are encoded using ASCII, which works well for English, but not so well for other languages
    - UTF-8 is now the global standard and can handle most characters used in the world today
    - readr uses UTF-8 universally, but this can fail if the data is produced by an older system that does not understand UTF-8
      - In order to correct for this you need to establish a locale and define the encoding method
        - E.g. parse_character(<x1>, locale = locale(encoding = 'Latin1'))
    - If you do not know the proper encoding (it is sometimes in the data documentation) then you can use readr's _guess_encoding()_ function to help you determine which type of encoding to use
      - The more text you have the better it does, and the higher the confidence will be
      - The first argument can be a file or a raw string
  - Factors:
    - Used to define a set of possible categorical values that the data must conform to
    - You must include a vector of known levels in order for _parse_vector()_ to generate a warning whenever a value does not match the criteria
      - E.g. fruit <- c('apple', 'banana')

parse_factor(c('apple', 'banana', 'bananas'), levels = fruit)

#> a warning regarding 'bananas' (too long to type total output)

  - Dates, Date-Times, and Times:
    - parse_datetime() expects the data to be in ISO8601 format, which is an international standard that arranges time from largest to smallest blocks, i.e. year, month, day, hour, minute, second
      - ISO8601 is the most imporant standard and most frequently used, if using it often it may be helpful to read the Wikipedia entry
    - parse_date() expects a four digit year, a - or /, the month, a - or /, then the day
    - parse_time() expects the hour, :, minutes, optionally :, and seconds, and an optinoal am/pm specifier
      - Base R's time data class is not very good, so we typically use the one provided in the hms package
    - If defauls don't work for your data then you can use the following components to define your own
      - Year:
        - %Y (4 digits)
        - %y (2 digits, 00-69 -> 2000-2069, 70-99 -> 1970-1999)
      - Month:
        - %m (2 digits)
        - %b (abbreviated name, like 'Jan')
        - %B (full name, 'January')
      - Day:
        - %d (2 digits)
        - %e (optional leading space)
      - Time:
        - %H (0-23 hour format)
        - %I (12 hour format, must be used with %p)
        - %p (am/pm indicator)
        - %M (minutes)
        - %S (integer seconds)
        - %OS (real seconds)
        - %Z (time zone, a name, not abbreviaitons)
        - %z (an offset from UTC, e.g. +0800)
      - Nondigits:
        - %. (skips one nondigit character)
        - %\* (skips any number of nondigit characters)
- Exercises on pg. 136
  - The locale argument will not allow you to set the decimal_mark and grouping_mark to the same mark
  - If decimal_mark = ',' then grouping_mark is set to '.' and vice versa (each one will alter the otherr accordingly)
  - Wikipedia has a list of common encodings that can be accessed if need be
- Parsing a File:
  - Strategy:
    - readr uses a heuristic to figure out the type of each column (using the first 1000 rows)
      - To view how this works you can use _guess_parser()_ to get readr's best guess, then _parse_guess()_ which uses the guess to parse the column in question
    - The heurstic tries each of the following types, stopping when it finds a match:
      - Logical, integer, double, number, time, date, date-time
      - If not of the parsers work properly, then it will remain a vector
  - Problems:
    - Defaults do not always work for larger files:
      - The first thousand rows may not be indicative of the entire dataset
      - The column may contain a lot of NA values, which will lead it to guess a character string
    - Every parse_\*() has a corresponding _column_\*()_ functions
      - parse_\*() is used when the data is a character vector is R already
      - column_\*() functions tell readr how to load the data
  - Other strategies:
    - You can include the argument _guess_max(<n>)_ in the read_\*() call in order to extend the guess beyond the 1000 value default
    - Sometimes it is easier to read in all columns as character vectors
      - If you then define a data frame (such as a tribble of your imported data) then you can use _type_convert()_ which will apply the heuristics to the character columns in the data frame itself
    - If reading a very large file you may want to set n_max to a smaller number (like 10,000) in order to work out the problems before importing the entire list
- Writing to a File:
  - To increase the probability of the output file being read correctly back in to the program is by using _write_csv()_ or _write_tsv()_:
    - They encode all strings with UTF-8
    - All dates are stored as ISO8601
  - If you wish to write a file so that it can be used in Excel, you can use _write_excel_csv()_
  - All of these write functions require the data frame to save and the path to save it, with the ability to specify the way to store na values
  - Type data can be lost in this writing process, so for interim results caching it is best to use functions like _write_rds()_ and _read_rds()_
    - These store data in R's proprietary binary format called RDS
  - _feather_ package includes a function that implements a fast binary file format that can be shared across programming languages:
    - _write_feather()_
    - feather does is typically faster than RDS and can be used outside of R, but does not currently support list-columns(chapter 20)
- Other types of data
  - _haven_ reads SPSS, SAS, and Stata files
  - _readxl_ reads Excel files (.xls and .xlsx)
  - _DBI_, along with a database-specific backend, allows you to run SQL queries against a database and return a data frame
  - _jsonlite_ for JSON files
  - _xml2_ for XML files

## Chapter 9 - Tidy Data with tidyr

- 'Tidy datasets are all alike, but every messy dataset is messy in its own way'
- To learn more about the theory: [http://www.jstatsoft.org/v59/i10/paper](http://www.jstatsoft.org/v59/i10/paper)
- Tidy Data:
  - Three main rules that make a data set tidy:
    - Each variable must have its own column
    - Each observation must have its own row
    - Each value must have its own cell
  - Two main advantages
    - If you have a standard structure then learning the tools that work with that structure allows you to apply them to other data sets
    - Putting variables in columns allows for the vectorized nature of R to shine
- Exercises on pg. 151
- Spreading and Gathering:
  - Many people are unfamiliar with tidy data, thus you will often encounter untidy data sets that you must use
  - Data is often organized for the ease of use in some application other than analytics (such as data entry)
  - Gathering:
    - A common problem is the having the column names appear as values of a variable, rather than the name of the variables themselves
    - _gather()_ :
      - Can be used to remedy this situation
      - Requires three parameters
        - The set of columns that represent values, not variables (the error columns basically)
        - The name of the variable whose values form the column names (what the appropriate column name should be)
        - The name of the variable whose values are spread over the cells (the values from the observation that has been mistakenly put on the column names,)
          - E.g. if 2000 and 2001 are placed as column names and you wish to use year (the variable) then the data from each year will be this third parameter, such as the number of homeruns a team had in that year
      - _gather(<error_column1>, <error_column_n>, key = <variable_name>, value = <values_for_observation>)_
    - Spreading:
      - Opposite of gathering, namely used to combine an observation spread over multiple rows
      - Requires two parameters instead of three:
        - The column that contains the variables names (key)
        - The column that contains the values from multiple variables (value)
      - _spread(<data_set>, key = <key_column_name>, value = <value_column_name>)_
- Exercises on pg. 157
  - spread() and gather() are not symetrical because the column type information is not transferred between them
  - If you have multiple rows for the same information, it will not sum or overwrite the values, it will return an error and fail the spread() or gather()
- Separating and Pull:
  - _separate()_ :
    - Pulls apart one column into multiple columns, by splitting wherever a separator character appears
    - By default it will split whenever it sees a non-numerical character
      - You can alter the default by passing the appropriate separator into the separate() function
    - The default output columns retain the column type of the original column from which they were pulled
      - Can be converted to better types by including the paramter _convert = TRUE_
    - If you pass a vector of integers to _sep_ then it will split the original from the specified position (positive numbers move from left to write, so _sep = 2_ would give you the leftmost 2 characters)
  - _unite()_ :
    - Combines multiple columns into one, which is much less common than separate()
    - It will default to adding an underscore between the combined values
      - Can be altered by passing the sep argument ('' for no separator)
- Exercises on pg. 160
  - _extra_ argument tells separate() what to do with the extra characters that may appear when separating, which defaults to dropping them entirely with a warning before the output
    - Can merge the extra values to other columns, etc.
  - _fill_ argument tells separate() how to handle too few arguments, its default is to place an NA value and give a warning
    - Can be altered to show the empty cell from either the right side or the left side (_fill = 'right'_)
- Missing Values:
  - Two ways for the data to be missing:
    - Explicitly, with markers such as NA
    - Implicitly, with the data simply not existing in the set
  - _complete()_ :
    - Useful for making implicit missing values explicit
    - Searchs a set of columns for all unique combinations and returns a NA value for those that have implicit missing values
  - _fill()_ :
    - For a column that has missing values but you wish for them to take the last nonmissing value and repeat it
    - Will take the last nonmissing value and will duplicate it for each NA value until the next nonmissing value appears
    - You can also alter the direction so that it will grab the next nonmissing (from below) value rather than the last nonmissing (from above)
- Case Study on pg. 163 with WHO data

## Chapter 10 - Relational Data with dplyr

- Three families of verbs designed to work with relational data:
  - Mutating joins: add new variables to one data frame from matching observation in another
  - Filtering joins: filter observation from one data frame based on whether or not they match an observation in the other table
  - Set operations: treat observations as if they were set elements
- Exercises on pg. 174
- Key:
  - Variables used to connect each pair of tables
  - Uniquely identifies each observation (row)
  - Primary: uniquely identifies an observation in its own table
  - Foreign: uniquely identifies an observation in another table
- One way to ensure that your keys are truly unique is to is count() and look for entries where n>1
- If a table has no primary key then you can add one with mutate() or row_number()
- Most relationships are one-to-many, but you can use 1-to-1, many-to-one and can do some work arounds to get many-to-many
- Mutating Joins:
  - _inner_join()_ : matches pairs of observations whenever their keys are equal
    - Unmatched rows are not included in the ouput
    - Very easy to lose observations, thus it is not always the best method to use in analysis
  - Outer Joins:
    - _left_join()_ : keeps all observations in x and adds some from y by matching the specified data frame to the original using _by = <column_name>_ to determine the key to use
    - _right_join()_ :keeps all observations in y and adds some from x
    - _full_join()_ : keeps all observations in x and y even if they have no match
- Defining the key columns:
  - Use the _by =_ argument to define which columns to use
  - by = defaults to NULL, which will use the so called 'natural join'
    - Matches all the variables that exist in both tables
  - by = <variable_name> will match the tables based on the defined column(s)
  - Named character vectors (like c('1', '2')) can be used to create a relationship between two tables that have different names for their columns, but that have matching values
- Exercises on pg. 186
- Other implementations:
  - _base::merge()_ : can perform the same four types of mutating joins
    - _merge(x, y)_ : inner join
    - _merge(x, y, all.x = TRUE)_ : left_join()
    - _merge(x, y, all.y = TRUE)_ : right_join()
    - _merge(x, y, all.x = TRUE, all.y = TRUE)_ : full_join()
  - Using dplyr verbs for joins makes code more readable than using merge()
  - SQL is the inspiration for the dplyr verbage
- Filtering Joins:
  - Filtering joins behave similarly to mutating joins, but they act on the observations, not the variables
  - Two types:
    - _semi_join(x, y)_ : keeps all observations in x that have a match in y
      - Useful for things like filtering a table based on the top/ bottom 10 of a certain variable without using a variable itself, rather using a calculated table that allows you to make multi-faceted filters
    - _anti_join(x, y)_ : drops all observations in x that have a match in y
      - Useful for diagnosing join mismatches
- Exercises on pg. 191
- Join Problems:
  - Data in this chapter has been cleaned and is relatively easy to use, whereas your own may not be, thus there are some important tips:
    - Identify the variables that form the primary key in each table
    - Check that none of the variables in the primary key are missing
    - Check that foreign keys match in other tables
      - Often due to data entry errors or poor methodology
- Set Operations:
  - Usually the least frequently used
  - Often used for breaking a complex filter into smaller parts
  - Operate on a complete row, comparing the values of every variable
  - Expects the x and y inputs to have the same variables and treats observations like sets
  - _intersect(x, y)_ : return only observations in both x and y
  - _union(x, y)_ : return unique observations in x and y
  - _setdiff(x, y)_ : return observations in x, but not in y

## Chapter 11 - Strings with stringr

- _Regexps_ : shorthand for regular expressions
- _stringr_ package : not part of the regular tidyverse package, so it should be loaded explicitly
- String Basics:
  - Created using either single quotes or double quotes, there is no difference in behavior (author recommends ')
  - If you do not close out a string it will display the continuation symbol in the console (a plus sign +)
  - To use a literal sinle or double quote, you can use \ to escape it like in Python
    - So if you wish to use a \, you must escape it with a \, ending with \\
  - Printed strings show the escapes, whereas using _writelines(<x>)_ will show the raw contents
  - Other special characters:
    - _\n_ : new line
    - _\t_ : new tab
  - Multiple strings are usually stored in a character vector which is created with _c(<string_1>, <string_n>)_
- _str_length()_ : tells you the number of characters in the string
- stringr functions begin with _str__, which makes them easier to remember and use, and also triggers autocomplete in RStudio
- _str_c(<x>, <y>, …)_ : used to combine two or more strings into one
  - Pass the (sep = ) argument in order to control how they are separated
  - Pass the _collapse =_ argument to collapse a vector into a single string
- NA values are contagious, so in order to print them as NA you can use _str_replace_na()_
- str_c() is vectorized, so it will lengthy the shorter strings to match the longest and will silently drop strings of length 0
- _str_sub()_ : extracts subsets of the string
  - Includes arguments for the _start_ and _end_ (inclusive)
  - Will return as much as possible if the string is shorter than the subsetting number
- _str_to_lower()_ : convert all to lowercase (can be swapped for upper as well)
  - Changing case can be tricky depending on the language
  - You must specify a locale using the ISO 639 language code, which is either a two or three letter abbreviation for a language
  - If the locale is blank it will default to your systems current locale
- _str_to_title()_ : changes strings to titles
- If you wish to make sure your sorting and ordering is robust and independent of the machine's locale, you can use _str_sort()_ and _str_order()_ to pass along a locale of your choosing, whereas base R doesn't allow for this
- Exercises on pg. 199
  - How do paste() and paste0() differ?
  - _str_wrap()_
  - _str_trim()_
- _Matching:_
  - _str_view()_ : takes a vector as the first argument then a text string, then matches the exact string
    - If you use a period it will match to any character except a new line
    - Anchoring:
      - ^ to match the start of a string
      - $ to match the end of a string
      - \b to match the boundary between words
    - \d matches any digit
    - \s matches any whitespace
    - [abc] matches a, b, or c
    - [^abc] matches anything except a, b, or c
- Exercises on pg. 204
- Repetition: you can specify the number of matches
  - ?: 0 or 1
  - +: 1 or more
  - \*: 0 or more
  - High precedence, so parentheses are preferred
  - {n}: exactly n
  - {n,}: n or more
  - {,m}: at most m
  - {n, m}: between n and m
- By default these functions are greedy (match the longest string possible) but they can be switched to lazy (shortest string matching) by using a ? after the matching terms
- Exercises on pg. 206
  - Solve regexp puzzle at [https://regexcrossword.com/challenges/beginner](https://regexcrossword.com/challenges/beginner)
- Grouping and Backreferences:
  - You can use \1, \2, \n to reference back to defined characters in a string searching function
    - E.g. (.)\1\1 would return any strings with three repeating characters like 'aaa' because (.) would reference any character and the two \1's would give you another (.) twice
- Detect Matches:
  - _str_detect()_ : to determine if a character vector matches a pattern
    - _E_.g. x <- c('apple', 'banana', 'pear')

str_detect(x, 'e')

    - Would return TRUE, FALSE, TRUE
  - _identical(<variable1>, <variable2>)_ : returns true if the two variables are the same (for example two functions that return lists of number 1-10 in different ways but both get the same output)
  - _str_subset(<data>, <regexp>)_ : returns the subset of the data that fulfill the logical requirement given by the regexp
  - _str_count(<data>, <regexp>)_ : returns the number of matches of the substring are in a string (like 3 a's in banana)
  - Matches never overlap
    - E.g. in 'abababa' 'aba' only repeats twice, not three times
  - Many stringer functions also have a pair that uses the __all_ suffix that will show all matches inside a string rather than just the first match
- Exercises on pg. 211
- Extract Matches:
  - _str_extract(<df>, <expression>)_ : usually a more complex expression is used when extracting
  - If you include the _simplify = TRUE_ inside of a _str_extract_all()_ then you can see all the matches (if multiple in a single observation) and their position relative to the other matches in a tibble
- Exercises on pg. 213
- Grouped Matches:
  - Return to 213 if needed, mostly just combines the above sections
- Replacing Matches:
  - _str_replace() and str_replace_all()_ : used to replace old strings with new ones
    - Without the _all it will only replace the first occurrence
    - If you wish to replace multiple things at once (like the numbers 1,2, and 3 with the words one, two and three) then you can use a named vector such as c('1' = 'one', '2' = 'two', '3' = 'three')
    - You can also use backreferences to inside the replacement function to do things like switching the order of the second and third words (from \\1 \\2 \\3 to \\1 \\3 \\2)
- Splitting:
  - _str_splot()_ : splits a string into component parts
    - Can use simplify = TRUE to return a matrix
    - Takes the delimiter as the first argument
    - E.g. a space would be str_split(' ')
    - You can also define the number of components you wish to return using the argument n = <n>
    - There is also an argument that allows you to split strings based on defined boundaries such as character, line, sentence, or word
- Exercises on pg. 217
- Finding Matches:
  - _str_locate()_ and _str_locate_all()_ : returns the starting and ending position of the matche(s)
- Other Types of Pattern:
  - When passing a regexp as an argument, it is essentially shorthand for the full writing which is: _regex('')_
  - You can pass arguments to the regex() function like:
    - _ignore_case = TRUE_ : ignore the case of the string
    - _multiline = TRUE_ : allows ^ and $ to match the start and end of each line rather than the start and end of a complete string
    - _comments = TRUE_ : use comments and white space to make complex regexps more understandable
      - Can use this to demonstrate what each step of a regexp means for example
    - _dotall = TRUE_ : allows . to match everything, including \n
  - Instead of regex() you can use:
    - _fixed()_ : matches exactly the specified sentence of bytes
      - Ignores all special regexps and operates at a very low level
      - This can be faster but will get you into trouble on languages other than the native English (or characters that have multiple representations like accents)
    - _coll()_ : compares strings using standard collation rules
      - Requires a locale as many places use different rules for collation
    - _boundary()_ : like above, used to separate based on boundaries
- Exercises on pg. 221
- Other Uses of Regular Expressions:
  - _apropos()_ : searches all objects available from the global environment
    - Useful for searching for names of functions that you can't quite remember
  - _dir()_ : lists all the files in a directory. The pattern argument takes a regexp and only returns filenames that match the pattern
- stringi:
  - stringer is built on top of the stringi package
  - stringer is beginner focused and limits the functions to 42, while stringi contains a whopping 234 and is far more comprehensive
- Exercises on pg. 222

## Chapter 12 – Factors with forcats

- Factors are used when working with categorical variables or when you wish to display character vectors in a non-alphabetical order
- Historically factors are easier to use that characters, so they often appear where you wouldn't expect and may not be the most useful
- Prerequisites:
  - Install the _forcats_ package (not part of the tidyverse)
- Creating Factors:
  - Begin with a list of valid levels
  - Each level is a unique factor
  - _factor(<variable>, levels = <variable2>)_
    - E.g. x1 <- c('Dec', 'Apr', 'Jan', 'Mar')

month_levels <- c('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec')

y1 <- factor(x1, levels = month_levels)

sort(y1)

#> Jan Mar Apr Dec

  - If there are items in variable1 which do not appear in the levels definition then they will be silently converted into NA
    - _parse_factor()_ : if you wish to receive an error rather than NA conversion
    - This is a readr function
  - If you omit the levels in the definition, it will take them automatically based on alphabetical order
  - _levels = unique(<variable>)_ : orders the levels based on their appearance in the raw data
  - _fct_inorder()_ : can use the pipe to push a factor into this function and return the items in order of appearance like above
- General Social Survey:
  - _dataframe %>% count(<variable>)_ : quick way to see which levels are in the df
  - If you wish to use a bar chart to do the same as above, it may be best to use the following addition in order to show the levels that may not have any observations but are part of the definition: _scale_x_discrete(drop = FA __LS__ E)_
- Modifying Factor Order:
  - _fct_reorder(<f>, <x>, <fun>)_ : takes the factors whose levels you want to modify f, the numeric vector that you want to use to reorder x, and an optional function that is used if there are multiple values of x for each value of f (default is median) fun
  - Reserve the factor reordering for factors which are arbitrarily ordered on their own, if there is an order it will create a messy visualization
  - _fct_relevel(<variable>, <factor>)_ : will move the specified factor to the beginning by default, but can pass a number to specific the number of positions to move forward
  - _fct_reorder2()_ : reorders the factor by the y values associated with the largest x values (basically makes the lines in a line graph match up with the legend order)
  - _fct_infreq()_ : order levels by increasing frequency (best for bar charts)
  - _fct_rev()_ : no description
- Exercises on pg. 232
- Modifying Factor Levels:
  - _fct_recode(<variable>, '<old>' = '<new>')_ : allows you to redefine each level with a new value
  - _fct_collapse()_ : if you need to collapse multiple old factors into one
    - _fct_collapse(<df>, <new_factor> = c(<old_1>,...,<old_n>),...)_
  - _fct_lump()_ : if you simply wish the lump together all the smaller groups
    - May lead to oversimplification
    - Also takes a second argument which is the number of groups which we to retain (e.g. _n = 10_ would be 10 groups)
  - Exercises on pg. 235

## Chapter 13 - Dates and Times with lubridate

- Three types of date/time data:
  - Date: the calendar day, tibbles print <date>
  - Time: usually to the nearest second, tibbles print <time>
  - Datetime: usually to the nearest second, tibbles print <dttm>
- R does not have a built in class for storing times, install the _hms_ package if needed
- _today()_ : returns the current date
- _now()_ : returns the current date time
- From Strings:
  - lubridate provides the ability to parse a date by simply arranging _y, m_ and _d_
    - _ymd()_ : year, month, day
    - _dmy()_ : day, month, year
    -
  - These lubridate functions can take either a date string, or unquoted numbers
  - In order to create a datetime, add an underscore and any combination/ordering of _h, m_ or _s_
    - _dmy_hms()_
  - You can also create a date time by specifying the timezone as the second argument of a date creation function
- From Individual Components:
  - _make_date()_ : allows for the creation of a date from several components (such as separate columns for hour, minute, and second
  - _make_datetime()_ : same as above, but includes a time component
  - Return to pg. 241 for a great use of a defined function, the pipe, and mutate to create multiple datetimes at once
- From Other Types:
  - _as_datetime()_ and _as_date()_ : returns the specified type
- Exercises on pg. 243
- Datetime Components:
  - Getting Components:
    - Using the _accessor_ function you can call out individual parts, like _year()_
    - For _month()_ and _wday()_ you can pass a second argument that when set to TRUE will return the abbreviated name of the month or weekday
  - Rounding:
    - _floor_date(), round_date(),_ and _ceiling_date()_ : returns the rounded date depending on which form of rounding is preferred
    - Not always super useful, but can be on occasion
  - Setting Components:
    - You can use accessor functions to set component values of a datetime
    - You can also use an _update()_ statement and pass along multiple changes at once
- Exercises on pg. 248
- Time Spans:
  - Duration:
    - Represents the true elapsed time value
    - In base R you can subtract two datetime to view duration, but it provides a difftime object, which can be hard to read
    - lubridate provides the _duration()_ function for this
    - _as.duration()_ : returns the duration
    - Multiple duration constructions, including:
      - _dseconds(), dminutes(), dhours(),..._
      - All these functions will return the duration in seconds, but will also display the duration as a rounding to the unit you have specified
        - g. _dminutes(10)_ returns '600s (~10 minutes)'
    - You must be careful with these functions, as they use an exact number of seconds, so leap days, daylight savings, etc. can alter your math
  - Periods:
    - Unlike durations, periods do not measure time by number of seconds, they use more human-like timeframes like days, weeks, and months
    - Created with simple functions like: _hours(), months(),_ and _years()_
    - You can easily add and subtract, multiply and divide periods
    - Periods can also be used to add/subtract/etc. to dates. This allows periods to be particularly useful
  - Intervals:
    - If you were to divide a year into its constituent days, you could receive two answers, 365 for most days, or 366 for leap years
    - To compensate for this, it is best to use an interval, which specifies the starting point
      - g. _next year <- today() + years(1)_

_(today() %--% next_year) / days(1)_

_#> 365_ #for a non-leap year of 2018

- Figure 13-1 on pg. 253 shows which arithmetic operators can act on each date/time type
- Exercises on pg. 253
- Time Zones:
  - R uses the IANA standards for defining time zones
    - Typically follows the pattern _<continent>/<city>_
    - Some exceptions, like _America/New_York_
  - All IANA items contain decades of time zone data
  - _sys.timezone()_ : returns the timezone R believes you are in
  - _olsonnames()_ : returns all timezone names
  - lubridate will use UTC unless otherwise specified

# Part 3 - Program

## Chapter 14 - Pipes with magrittr

- Packages in the tidyverse call the %>% automatically, but if you are not loading of these packages, you must call it _magrittr_ explicitly
- Piping Alternatives:
  - Intermediate steps:
    - Save each step as a new element that uses the previous element as an input
    - If there are lots of natural names for each step then this is quite clean
    - If there aren't natural names, then your code will be cluttered with unneeded names and each suffix will need to be incremented properly
    - You may think this would store lots of new objects as we create variable after variable, but this is not the case. R will find relations and reference them rather than completely copy them (such as if you define a new df with an added column, the only added storage is the new column)
    - _pryr::object_size()_ : returns the memory size of the object that is passed as an argument, or the total if there is more than one object
  - Overwrite the Original:
    - This is cleaner and faster than intermediate steps, but it makes debugging much more difficult and the readability is not the best as we repeat ourselves regularly
  - Function Composition:
    - This is hard for most people to read, considering you now must read the code from inside out, rather than left to right like normal
    - It also separates argument as you include more layers
  - Use the Pipe:
    - Focuses on the set of imperative operations, with the next step clearly detailed and the arguments tied closely together
    - Lexical transformation: magrittr reassembles the code in the pipe to a form that work by overwriting intermediate objects
    - This means that the pipe cannot work on 2 different kinds of functions:
      - Those that use the current environment (such as assigning a new value to a variable that is already defined)
      - Those that use lazy evaluation. These would be functions that do no compute arguments until the function is called
        - g. _tryCatch(), try(), suppressMessages(),_ etc.
- When Not to Use the Pipe:
  - Your pipes are longer than 10 steps (in general)
  - If you have multiple inputs or outputs
  - You are conceptualizing a directed graph with a complex dependency structure
- Other Tools from magrittr
  - When working with complex pipes, you may want to call a function for its side effects (like printing), in this instance, you need to use a T pipe: _%T>%_
    - Essentially calls the left side of an assignment (like the variable name that would then be passed to a print function)
  - When working with functions that don't have a data frame-based API, the exploding pipe may be useful: _%$%_
    - Explodes the variable that is passed to it and allows for explicit reference
  - For assignment and modification, use the assignment pipe: _%<>%I_
    - Allows you to assign a set of operations to a dataframe without requiring an explicit assignment call
      - g. _mtcars <- mtcars %>%_

_transform(cyl = cyl \*2)_

Would be:

_Mtcars %<>% transform(cyl = cyl \*2)_

## Chapter 15 - Functions

- Three primary advantages of writing functions:
  - Assign an evocative name that makes code easier to read
  - Only requires code changes in one location that then propagate elsewhere
  - Eliminates the chance of making incidental mistakes when copying and pasting
- When Should You Write a Function?
  - If you have three or more copies of the same code block
  - You need to do 3 things:
    - Pick a descriptive name
    - List the inputs (arguments) to the function inside the _function_ call
      - g. _function(x, y, z)_
    - Place the developed code into the body of the function
      - This body is defined by curly brackets
- Exercises on pg. 273
- Functions are for Human and Computers:
  - Try to stick with a single format (snake_case is usually better)
  - If there is a family of functions, try to prefix them with the same word (if they require more than one word) for easier autocompletion
  - Try to avoid overriding existing functions and variables
  - Remember to comment chunks of code to explain the 'why' of that code unit
    - Created in RStudio with CTRL+SHIFT+R
    - Shown in the navigation dropdown at the bottom left of the screen
- Exercises on pg. 276
- Conditional Execution:
  - _if_ statements allow you to conditionally execute code
    - _if (<condition>) { executed when true } else { executed when false }_
  - Conditions:
    - Must evaluate to TRUE or FALSE
    - Multiple logical expressions can be combined with || or &amp;&amp;
      - These functions are 'short-circuiting'
        - Once || sees the first TRUE it will return TRUE
        - Once &amp;&amp; sees the first FALSE it will return FALSE
    - Cannot pass vectors to the condition, it must be collapsed with either _all()_ or _any()_, which will return a single value
    - _identical()_ : Boolean type that is very strict about types and values
      - g. _identical(0L, 0) = FALSE_
  - Multiple Conditions:
    - Chaining many if statements is usually a good indicator that you need to rewrite
    - Functions like the _switch()_ can be helpful with this
    - _cut()_ : use to discretize continuous variables
- Exercise on pg. 279
- Function Arguments:
  - Arguments typically fall into two broad categories:
    - The data to compute on
    - Details that control the computation
  - Generally, the data arguments should be first with the details at the end
  - The details arguments should also pass along a default value
  - Choosing Names:
    - Default to longer and more descriptive names
    - Some common, short names:
      - x, y, z: vectors
      - w: weights vector
      - df: data frame
      - i, j: numeric indices
      - n: length or number of rows
      - p: number of columns
  - Checking Values:
    - It is important to check high importance preconditions with errors if they are not met (with functions like _stop()_)
    - Some arguments do not need to be specifically checked, especially if you know the exact shape of your data inputs
    - You can combine several argument checks into one with _stopifnot()_
      - This way you can check that each argument meets a certain logical condition and will return an error if any condition is not met
  - Dot-Dot-Dot (...):
    - Many R functions can take an arbitrary number of inputs with the (...) argument
- Exercise on pg. 285
- Return Values:
  - Two primary considerations:
    - Does returning early make your function easier to read?
    - Can you make your function pipeable?
  - Explicit Return Statements:
    - The value returned is typically the last value computed, however, you can call _return()_ to get the value earlier in the code
    - return() really should be reserved for instances in which you can use a simpler form of calculation (for instance, when you have 10 lines of code to calculate, but if one of the arguments is 0 then you know you only have to run 3 lines of code, you can use the return() to get this value without as much computational effort)
    - It is most common to have an if statement that contains one complex block of code and one simple, the simple function can then return() the value with less computation involved
  - Writing Pipeable Functions:
    - Two main types of pipeable functions:
      - Transformations
        - A primary object that is passed in and a modified version is returned by the function
      - Side-effects
- Environment:
  - Lexical scoping: used by R to find the value associated with a name
  - If a name is not defined inside a function for example, R will search the environment to find the value that should be used for calculation
  - This allows you to do things like define the addition symbol as a completely separate function (like subtraction instead) without R telling you that this is not possible

## Chapter 16 - Vectors

- So far we have focused primarily on tibbles, but they are based on vectors
- Vectors are a component of the base R package, so they do not require additional packages to be installed, however, many people use the _purrr_ package
- Vector Basics:
  - Two main types:
    - Atomic: contain 6 subtypes
      - Logical, integer, double, character, complex, and raw
    - Lists: often called recursive vectors
  - The primary difference is that atomic vectors must be homogeneous, whereas lists may be heterogeneous
  - Null is yet another related topic, and is essentially the absence of a vector
  - Every vector has two key properties: the type and the length
  - Vectors may also contain arbitrary metadata known as attributes which build additional behavior onto the original behavior
  - Augmented vectors:
    - Factors are built on top of integer vectors
    - Dates and date-times are built on top of numeric vectors
    - Data frames and tibbles are built on top of lists
- Atomic Vectors:
  - Logical:
    - Only has three possible values: TRUE, FALSE, NA
    - Regularly constructed with comparison operators
  - Numeric:
    - Contains both integer and double vectors
    - R defaults to doubles, in order to make an integer you must put an L behind the number
    - Double are approximations, they represent floating-point numbers that have the same precision problem that all floats have
    - When comparing floats you can use _dplyr::near()_ to allow for some numerical tolerance instead of the absolute _==_
    - Integers have the special _NA_ value
    - Doubles have 4 special values: _NA, NaN, Inf, -Inf_
      - You can use _is.finite(), is.infinite(),_ or _is.nan()_ for checking for these values rather than using the ==
  - Character:
    - R stores each string as part of a global string pool, creating references to the object rather than duplicates of it (this saves memory as a pointer is only 8 bytes)
- Exercises on pg. 296
- Using Atomic Vectors:
  - Coercion:
    - Explicit coercion occurs when you call a function like _as.integer()_
    - Implicit coercion happens when you use a vector in a specific context that expects a certain type of vector
      - g. summing a logical vector would provide the number of true values as it is automatically converted to a 1 for each TRUE
    - When trying to create a vector in c(), the most complex type will always win
  - Test Functions:
    - _typeof()_ : returns the vector type
    - _purrr_ contains many tests for type such as _is.numeric()_
  - All types of vectors can be named with c()
    - You can also use _purrr::set_names()_
  - You can use subsetting on vectors much like calling an offset position in Python (except the first element in R is 1 not 0)
    - Negative values will drop the elements at the defined positions
  - If you have a named vector (essentially a dictionary) then you can use the name to subset the vector
- Exercise on pg. 302
- Recursive Vectors (Lists):
  - _str()_ : focused on the structure of the list, showing the content as well as the format
  - [] can be used to subset a string (like Python)
  - [[]] when used with a list will only return a single vector, and is a drill down rather than a new object (which is what [] creates)
- Exercises on pg. 306
- Attributes:
  - Essentially a named list of vectors that can be attached to any object
  - These can be assigned with _attr()_ and viewed with _attributes()_
  - 3 important attributes for implementing fundamental aspects of R;
    - Names: used to name the elements of a vector
    - Dimensions: make a vector behave like a matrix or array
    - Class: used to implement the S3 object-oriented system
  - Generic functions: functions which behave differently for different classes of input
    - Fundamental to object-oriented programming (like polymorphism in Python)
    - To view all methods that affect a generic function can be called with _methods()_
    - To view the specific implementation of a method, use _getS3method()_
      - This will show exactly how that specific method for that function works
- Augmented Vectors:
  - More complex vectors like dates and factors
  - Vectors that contain additional attributes
  - Four important augmented vectors are covered in this book:
    - Factors:
      - Built on integers with a levels attribute to represent categorical data
    - Dates and Times:
      - Numeric vector that represent the number of days since January 1, 1970
      - Datetime is a numeric vector of class POSIXct that are the number of seconds from the same date
        - POSIXct stands for 'Portable Operating System Interface,' calendar time
      - Can also add the _tzone_ attribute that changes how the datetime is printed, but not the absolute time reference
      - May also find POSIXlt types, but they are rare in the tidyverse and are easier to convert and use the built in _lubridate_ functions
    - Tibbles:
      - Built on lists and have three classes: _tbl_df, tbl,_ and _data.frame_
      - Two attributes: _(column) names_ and _row.names_
- Exercises on pg. 312

## Chapter 17 - Iteration with purr

- For loops:
  - Always contains three components:
    - Output:
      - _Output <- vector ('double', length(x))_
      - This type of assignment is giving the output sufficient space
      - Common to use vector, which contains two arguments: data type and length of the vector
    - Sequence:
      - _i in seq_along(df)_
      - Determines what to loop over
      - _seq_along_ is similar to _1:length(l)_ but safer and will return a blank return if you have a zero length vector
    - Body:
      - _output[[i]] <- median(df[[i]])_
      - The piece of code that actually iterates
- Exercises on pg. 316
- For Loop Variations:
  - Four variations on the basic theme of a for loop:
    - Modifying an existing object
    - Looping over names or values
    - Handling outputs of unknown length
    - Handling sequences of unknown length
- Exercises on pg. 321
- For Loops vs. Functionals
  - Sometimes you may use boilerplate language like that in the for loop over and over, which likely means you can rewrite it such that redundancy is at a minimum
  - One key way to do this is to pass the function in along with your data set, this way you can reuse the for loop and run different functions in the same manner (like finding the average over a column and the standard deviation later on)
- Exercises on pg. 324
- The Map Functions:
  - _map()_ : list
  - _map_lgl()_ : logical vector
  -
  - All purr functions are written in C, so they are a bit faster but are slightly less readable
  - The second argument (.f or function) can be a formula, character vector, or an integer vector
  - _map_\*()_ uses … to pass along additional arguments to the function (.f) each time it's called
- Shortcuts for _map()_ on pg. 326-327
- Exercises on pg. 328
- _safely()_ : used as a wrapper to always return your output, but will also return an error value
  - It will appear as output and a null error value if the function succeeds, or a null output and an error text if it fails
- _possibly()_ :behaves similar to safely(), but always succeeds and will return a predetermined error value if the inner function fails
- _map2()_ : can be used to iterate over two vectors in parallel (for example, the mean of a random generated list while varying the standard deviation)
- You could imagine a _map3()_ or _map4()_ but purr provides the function _pmap()_ that takes a list of arguments instead. This allows for as many arguments as you wish and is essentially a giant for loop wrapper
  - Because this can become hard to read, it is good practice to name your arguments (like mean = m)
  - The arguments and their constituents can also be passed along as a tibble (like on pg. 334)
- Invoking Different Functions:
  - There are times where you may want to vary the function in a similar manner to params
  - _invoke_map()_ is used to vary the function and is passed at least 2 arguments:
    - A set of functions or character map of functions
    - The params
    - All subsequent arguments are passed on to each function
  - In this way, you effectively make a mapping of each function, the params for each function, and any arguments that are consistent across all functions
- _walk(), walk2(), and pwalk()_ are all ways to effectively invisibly return a functions side effects, not the return values
  - g. saving a value to disk rather than outputting the value
- Other Patterns of For Loops:
  - Predicate Functions:
    - Predicate functions return one value that is either TRUE or FALSE
    - _keep()_ and _discard()_ can be used with predicate functions to store or remove the related value
    - _some()_ and _any()_ are used to determine if the predicate is true for any or for all of the elements
    - _detect()_ finds the first element where the predicate is true
    - _detect_index()_ returns the position of the detected object
    - _head_while()_ and _tail_while()_ take elements from the start or end of a vector while a predicate is true
  - Reduce and Accumulate:
    - _reduce()_ is used to join multiple data frames together in different ways:
      - _full_join_ is similar to an outer join in SQL
      - _intersect_ is limited to those elements which are shared across all df's
    - _accumulate()_ is used to store all of the interim results of a binary function (a function with two primary inputs)
- Exercises on pg. 338

# Part 4 - Model

## Chapter 18 - Model Basics with modelr

- The goal of a model is to provide a simple, low-dimensional summary of a dataset
- A fitted model is the closest model from a family of models (for example, y=4x is a specific model from the family of linear models)
- Just because you have the best fitted model does not mean that your model is good as well
  - As such, the real goal of a model is not to find the truth, but to find an approximation that is useful
- A Simple Model:
  - Using the example of linear regression, we can see how gradient descent is used in optimizing the model to best fit the data
  - _optim()_ : used to find the optimum model using the Newton-Raphson search
  - _lm()_ : similar to optim() but used exclusively on linear models (uses a similar technique but with a more specific and thus faster algorithm)
- Exercises on pg. 353
- Visualizing Models:
  - _data_grid()_ : takes a data frame as a first argument and each subsequent argument it finds the unique variables and then generates all combinations
  - _add_predictions()_ : takes a data frame and a model and displays the predictions of the model
  - _add_residuals()_ : much like add_predictions() but using the original dataset, not the grid
- Exercises on pg. 358
- Formulas and Model Families:
  - _model_matrix()_ : takes a df and a formula and returns a tibble of the values for the model equation
    - Adding additional aspects to the formula will grow the resulting tibble
  - Categorical Variables:
    - These will be calculated based on a the existence of a category (1 = yes, 0 = no)
  - Return to pg. 363 for interactions between continuous and categorical variables, as well as two continuous on the following page
  - _seq_range()_ : used to select a regularly spaced grid of values rather than every value
    - _pretty = TRUE_ : argument to make the selection more pleasing to the human eye
    - _trim = 0.1_ : will trim off 10% of the tail values (helpful for reducing bias in data sets with long tails away from the center)
    - _expand = 0.1_ : opposite of the trim argument
  - Transformations:
    - To wrap a formula transformation you must use _I()_, otherwise R will evaluate the functions as part of the formula expression
      - g. _y ~ x + I(x ^ 2)_ becomes _y = a_1 + a_2 \* x + a_3 \* x^2_
        - Without the I, it would become _y ~ x \* x + x_, which would turn to _y ~ x_ when R drops the redundant _x \* x_ (which represents x's interaction with itself). This would then be _y = a_1 + a_2 \* x_
    - _poly()_ : used to speed up the typing of a polynomial sequence
      - g. _poly(x, 2)_ would turn into _y = a_1 + a_2 \* x + a_3 \* x^2_
      - This does have the negative effect of rapidly shooting off to positive or negative infinity when outside the range of data
    - _spline()_ : used in place of poly() to provide much the same functionality without the rapid expansion
- Exercises on pg. 371
- Missing Values:
  - Modeling functions in R default to removing missing values silently, but you can modify this to print out a warning if so desired with _options(na.action = na.warn)_
  - You can also see how many observation were used with _nobs()_
- Other Model Families:
  - _stats::glm()_ : generalized linear models
  - _mgcv::gam()_ : generalized additive models
  - _glmnet::glmnet()_ : penalized linear models
  - _MASS::rlm()_ : robust linear models
  - _rpart::rpart()_ : trees
  - Return to pg. 372 for details on each family

## Chapter 19 - Model Building

- Long example using the diamond data set from earlier
- Exercises on pg. 384
- Long example using the flights data set from earlier
- Exercises on pg. 395

## Chapter 20 - Many Models with purr and broom

- Gapmindr data:
  - Summarizes progression of countries over time in things like life expectancy and GDP
  - This example is looking at life expectancy over time
  - The data has a general trend upwards over time, so to see the subtler trends, we should remove the linear trend and observe the residuals
  - This is easy to do for one country, but what about every other one?
  - Nested Data:
    - In order to extrapolate to multiple countries, we need to modify the code written on pg. 400 and write it as a function
    - This function will require that we operate on a subset of the full df, because each country may have more than one observation in the df
    - In order to use the data, we must create a nested structure
    - This can be done by first grouping the df, then passing that into the nest() function
    - _nest()_ : takes the grouped data and provides a new df that contains a list of smaller df's for each of the nested variable
      - Effectively a roll-up like a Pivot Table
  - List-Columns:
    - Now that we have a nested df, and a function that calls the model per country, we can use map() to apply the function on each country
    - Rather than running the function and outputting the regression parameters to a new object, it makes sense to store each value in the original nested df
    - To do this, we will use mutate() and store the output of the model in the nested df
    - This has the advantage of storing the metadata with the correct variables, whereas if we stored it as a separate object we would need to maintain the ordering so as not to return the wrong data in other areas
  - Unnesting:
    - In order to do things like plot the residuals of the df (which can be added using mutate() and mpa2() like with the model), we need to unnest the df
    - _unnest()_ : the inverse of nest(), allows for unnesting of a nested df as well as any list-columns that have been added during nesting
- Model Quality:
  - The _broom_ package provides tools to assess model quality by converting it to tidy data
  - _broom::glance()_ : extracts model quality metrics into a single row df
  - It is possible to add this model quality data to the unnested df by using map() to apply glance() to each iteration, mutate() to add this to the df, and unnest() to put it on each row
- Exercises on pg. 408
- List-Columns:
  - Generally there are three parts to an effective list-column pipeline:
    - Creating List-Columns:
      - Generally done with one of three methods:
        - _tidyr::nest()_ to convert a grouped df into a nested df where you have a list-column of other df's
        - _mutate()_ and vectorized functions that return a list
        - _summarize()_ and summary functions that return multiple results
      - They may also be made from a named list using _tibble::enframe_
      - nest() can use a grouped df and will retain the variables which are grouped in the resulting df, or you can pass along the variables you wish to nest (unnamed columns will not nest)
    - You create intermediate list-columns
    - Simplifying List-Columns:
      - When collapsing a list column back to a regular column, you can use mutate() with _map_lgl(), map_int(), map_dbl(), map_chr()_ to create atomic vectors
      - unnest() does the same thing but with multiple values rather than a single value
- Making Tidy Data with broom:
  - _broom::glance()_ : returns a single row for each model that contains certain model quality measures or a measure of model complexity
  - _broom::tidy()_ : returns a row for each coefficient in the model with columns giving estimates and variability
  - _broom::augment()_ : returns a row for each row in the data, adding extra values like residuals and influence statistics
  - Supports many model types from the most popular modeling packages

# Part 5 - Communicate

## Chapter 21 - R Markdown

- R Markdown provides a unified authoring framework for data science
- Combines code, results, and commentary
- Supports dozens of output formats
- Many of the features are from multiple different packages and tools and thus the ? operator doesn't always return documentation. Instead, it can be found in the cheatsheets area of help
- Each notebook chunk can be run independently with Ctrl+Shift+Enter
- To run the whole notebook and get an output, you can use the Knit button in the IDE or use the function _rmarkdown::render('<file>')_
  - This will show the file in the viewer and create an HTML file for sharing
- The general flow would be: Rmd file -> knitr -> md file -> pandoc -> end file
- Exercises on pg. 426
- Text Formatting with Markdown:
  - \*italic\* or _italic_
  - \*\*bold\*\* or _bold_
  - 'Code'
  - superscript^2^
  - subscript~2~
  - # 1st level header
  - ## 2nd level header
  - ### 3rd level header
  - \* bulleted list item
  - numbered list item
  - <link>
  - [linked phrase](link)
  - ![optional caption text](path to image)
- Exercises on pg. 428
- Code Chunks:
  - Can be inserted in three ways:
    - Ctrl+Alt+I
    - Insert button in the editor
    - Manually typing chunk delimiters '''{r} <code>'''
  - Chunks can also be given a name by including it in the {r} callout
    - g. '''{r example name}'''
  - Have several options that can be included in the {r} callout along with the name:
    - _eval = FALSE_ : prevents code evaluation, useful for displaying example code or disabling blocks
    - _include = FALSE_ : runs code but doesn't show the results or code in the final doc
    - _echo = FALSE_ : prevents the code from appearing but shows the result in the final doc
    - _message = FALSE_ or _warning = FALSE_ : prevents messages or warning from appearing in the final doc
    - _results = 'hide'_ : hides the printed output
    - _fig.show = 'hide'_ : hides the plot
    - _error = TRUE_ : causes the render to continue even if the code returns an error (defaults to error = FALSE and will stop the knitting)
- Tables:
  - By default, R Markdown shows tables as they would be shown in the console
  - _knitr::kable()_ : generates a table with formatting options
  - Other tools are available, like: xtable, stargazer, pander, tables, and ascii
- Caching:
  - Because each knit starts from a blank slate, there are some larger functions that require lots of time. To compensate for this, you may use _cache = TRUE_ to store the results of a chunk in a specific file on disk. Once executed, R will see if the code has changed, and if not, it will use the cached data for speed
  - This must be used carefully, as it looks exclusively at the code changes, not the dependency changes
  - This can be avoided if you use the _dependson = '<chunk(s)>'_ argument
    - Will accept multiple chunks and knitr will look at them all, if any changes are made then it will not use the cached data
  - Additionally, if the file itself changes, it will not reevaluate
    - However, if you use the _cache.extra_ and _file.info()_ functions in conjunction, you can capture the changes to the document (with file info, as it contains the last modified datetime) and recache when needed
- Inline Code:
  - You can imbed R code in the text chunks by using _'r <code>'_
- Exercises on pg. 434
- YAML Header:
  - Stands for 'yet another markdown language'
  - Parameters:
    - _params_ : used to pass along a value that will be used in the calculation (like a slicer in Excel)
    - You can write atomic vectors directly or run arbitrary R expressions with _!r_
      - g. _startdate: !r lubridate::ymd('2015-01-01')_
    - Parameters can also be passed as a tibble (see pg. 437)
- Bibliographies and Citations:
  - Pandoc can automatically generate citations and bibliographies in a number of styles
  - Return to pg. 438 for details

## Chapter 22 - Graphics for Communication with ggplot2

- ggplot2 provides several functions for adding text to visuals
- _labs()_ :
  - Including title, subtitle and caption
  - Can also be used to rename variable names
  - Additionally, mathematical notation can be used in place of text
- Exercises on pg. 445
- _geom_text()_ : similar to geom_point() but includes the label argument
- _geom_label()_ : adds a rectangle behind the text that would be seen in geom_text()
- ggrepel package offers functions to help apply transformations to labels (like a line connecting the label and point, or making sure no labels overlap)
- Another good way to distinguish data is to redraw the graph with the data you wish to highlight on top of the existing plot with different formatting
  - g. a plot with red dots is the base, a new plot with black circles surrounds the points that you want to highlight
- It's also possible to add a simple text label in the plot area by defining the location and formatting
  - See pg. 449 for example
- _stringr::str_wrap()_ : allows for a single line of text to be broken into multiple lines based on the number of characters per line
- Exercises on pg. 451
- Scales can be defined if so chosen
  - ggplot does this automatically, but they can be overwritten
  - g. _scale_x_discrete()_
  - Follow the format of scale, _, variable, _, type of scale
  - Inside the scale, you can redefine the breaks (tick marks) and the values associated with them
    - g. _scale_x_continuous(breaks = seq(15, 40, by = 5))_ would create a continuous scale in the x variable starting at 15, ending at 40, and counting up by 5
  - Breaks can be defined using a parameter (such as a selection of dates like holidays rather than every day of the year)
- Legends can also be modified in their layout and position with _theme(legend.position = '<location>')_
- Color can be modified using _scale_colour_manual(values = c(<variable_1> = '<color_1>', <variable_n> = '<color_n>'))_
- Exercises on pg. 460
- Changing the plot limits can be done in three ways:
  - Adjusting the data that is plotted
  - Setting the limits with a scale
  - Setting the xlim and ylim in _coord_cartesian_
- In the case of having multiple plots but each one has different scales (due to the sample), you could either limit the x and y in coord_cartesian or you could pass along the full scale of the whole data set
  - g. _scale_x_continuous(limits = range(<full_data_set>))_
  - This will force all the plots to use the same range, even if the samples are different
- 263 contains the 8 default themes for ggplot2
- Figure sizing is controlled with five main options and is preferable to do manually in R Markdown so as to have reproducible and consistent code
  - _Fig.width, fig.height, fig.asp, out.width, out.height_
- The out.width option uses the line width to determine the size (you pass along a percentage of the line width)
- _fig.align_ : determines the positioning relative to the line
- The code chunk name is the name used when storing graphics on disk, so it is important to get in the habit of naming chunks with graphics at the very least

## Chapter 23 - R Markdown Formats

- Two ways to set the output of the rmd file:
  - Permanently using the YAML header
    - g. _output: html_document_
  - Transiently by calling _rmarkdown::render()_
    - g. _rmarkdown::render(_

_'<filename>.Rmd',_

_output_format = '<type>'_

_)_

- The knit button also allows for the rendering of certain file types (but is only for that render)
- You can also render to multiple outputs by providing a list of the desired formats
- Common document types:
  - _pdf_document_
  - _word_document_
  - _odt_document_ (Open Document Text)
  - _rtf_document_ (Rich Text Format)
  - _md_document_
  - _github_document_ (tailored version of md_document designed for sharing on GitHub)
- Another important file type is _html_notebook_
  - This will keep all the source code and can be used to generate the Rmd file that made it, thus allowing for collaboration and sharing of source code
- Presentation formats on pg. 472
- _flexdashboards_ is a package that allows for the easy generation of dashboards
- Any HTML format may contain interactive components like maps and filters
  - _htmlwidgets_ are R functions that allow for the creation of of HTML visualizations
  - Many packages include htmlwidgets:
    - _dygraphs_ (time series)
    - _DT_ (tables)
    - _rthreejs_ (3D plots)
    - _DiagrammeR_ (diagrams like flow charts)
- HTML interactivity is all in browser, so no R code is actually called, which is good and bad
- To use interactive R code you can use _shiny_
  - To include this in R Markdown include the option _runtime: shiny_
  - This allows for 'input' functions to be used
- Other packages:
  - _bookdown_ (book publishing)
  - _prettydoc_ (lightweight document formats in a range of themes)
  - _rticles_ (formats tailored for scientific journals)
- Recommended reading on pg. 478

## Chapter 24 - R Markdown Workflow

- Shares many goals with a typical lab notebook:
  - Records what was done and why
  - Supports rigorous thinking (continuous reflection and analysis of your own methodology)
  - Helps others understand your work and process
- Tips for effective notebook use:
  - Ensure each notebook has a descriptive title
  - Use the YAML header for dating
  - Don't delete failed experiments, note it in the notebook and explain why it failed
  - Data entry is generally better outside of R
  - If you find an error, write code and an explanation of why you changed it, don't change it directly as it will be missed
  - Make sure you can knit the document when done with your session
  - Long run reproducibility may require version tracking for the packages used
    - _packrat_ package may be used to store the packages in the project directory
    - _checkpoint_ package will reinstall packages available on the date specified
    - Another method is to include a code chunk that runs _sessionInfo()_ which won't easily recreate packages, but will at least let you know what they were at the time
  - Naming schemes and project based storage will be crucial for storing the many projects that will inevitably be created