# stock-analysis

## Overview of Project
In this project, we have looked at data from 12 the stocks of 12 different green energy companiesto compare and determine which is best suited for Steve's investment. This analysis includes a look at the years 2018 and 2018, and includes both the total daily volume as well as the net return on each of these stocks for these years. With this info, Steve can make a more informed decision on his investment in green energy.

This analysis also covers re-factoring code. Re-factoring is a method of editing code to make it more efficient and faster. Code was written for this project, and then refactored in order to examine this method and determine its pros and cons.

## Analysis and Challenges
### Analysis of Results
The results from each of the 12 green energy stocks can be seen below:

![2017_stocks.png](https://github.com/bchillman/stock-analysis/blob/main/Resources/2017_stocks.JPG)
![2018_stocks.png](https://github.com/bchillman/stock-analysis/blob/main/Resources/2018_stocks.JPG)

DQ, the stock Steve was initially interested in, had low total volume in both years, and while it had an extremely successful return in 2017, had the worst performance in 2018. This volatility may indicate that it is not the strongest option for Steve's investments. In general, green energy stocks were very successful in 2017, but not at all in 2018, as only two stocks finished with a positive return (ENPH and RUN). Further analysis and understanding of the green energy sector would be needed to understand this trend and whether it is likely to continue on into 2019 and the future.

### Analysis of Refactoring
The code used to run these analyses was particularly inefficient as it contained a nested for loop, which adds a considerable amount of time to the process. Once this code was completed and shown to work, it was re-factored (or edited to make more efficient). This was done mainly with the help of an index variable, which we called *tickerIndex*. This index variable utilized the fact that the data was stored in such a way that it contained all of the data for an individual stock before moving onto the next (e.g. all of the AY data was in the first rows of the spreadsheet, followed by all of the CSIQ data, etc.). The index utilized this fact to not check which stock's data was in each row, but instead know it was still in the same stock until we hit the threshold point. The code for this is shown here:
![ticker_plus.png](https://github.com/bchillman/stock-analysis/blob/main/Resources/ticker_plus.JPG)
Thus, by knowing the order of the stocks, as we move through the rows, once the stock on one row is not the same as the next, we can tell the program to just move onto the next ticker. This greatly increases the efficiency as the program only needs one for loop, instead of the nested for loop, which means it has ~12 times fewer conditionals to check. To demonstrate this, this initial analysis took about **0.9 seconds** to run for a given year. The new, refactored code had the times shown below for each year.

<img src="https://github.com/bchillman/stock-analysis/blob/main/Resources/2017_time.JPG" width=25% height=40%>
<img src="https://github.com/bchillman/stock-analysis/blob/main/Resources/2018_time.JPG" width=25% height=40%>

These times are significantly lower than previously and demonstrate that this refactored code is more efficient.
