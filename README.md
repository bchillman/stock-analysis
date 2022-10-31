# stock-analysis
Note: In the directions for this challenge, it consistently mentioned using the years "2018 and 2018." I took this to mean "2017 and 2018," but I could have misunderstood the intent.

## Overview of Project
In this project, we have looked at data from 12 the stocks of 12 different green energy companies to compare and determine which is best suited for Steve's investment. This analysis includes a look at the years 2017 and 2018, and includes both the total daily volume as well as the net return on each of these stocks for these years. With this info, Steve can make a more informed decision on his investment in green energy.

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
Thus, by knowing the order of the stocks, as we move through the rows, once the stock on one row is not the same as the next, we can tell the program to just move onto the next ticker. This greatly increases the efficiency as the program only needs one for loop, instead of the nested for loop, which means it has ~12 times fewer conditionals to check. To demonstrate this, the original analysis took about **0.9 seconds** to run for a given year. The new, refactored code had the times shown below for each year.

<p align="center">
<img src="https://github.com/bchillman/stock-analysis/blob/main/Resources/VBA_Challenge_2017.JPG" width=25% height=40%> <img src="https://github.com/bchillman/stock-analysis/blob/main/Resources/VBA_Challenge_2018.JPG" width=25% height=40%>
</p>

These times are significantly lower than previously and demonstrate that this refactored code is more efficient and was successful.

### Challenges
There were two challenges I had in this weeks challenge. First came from trying to understand the tickerIndex and why it was making the code more efficient. Once I fully went through the challenge and looked back at what I had done I realized that we had done away with one of the for loops utilizing our understanding of how the data was sorted. My second challenge came from debugging a typo. When I was outputting the data onto the spreadsheet, I was intending to write this code:

<p align="center">
<img src="https://github.com/bchillman/stock-analysis/blob/main/Resources/typo.JPG" width=100% height=100%> 
</p>

Instead on the second and third outputs (where the results of the data were supposed to go, I had typed 1's instead of i's. This led to confusing results, as I had also not cleared the sheet before doing this, so it still had the correct results from the original, unrefactored, code. The sheet then had the results of everything being correct except for the second stock which had numbers that were not correct. Eventually through commenting out and attempting to debug various parts of the code, I discovered the issue and fixed the code.

## Summary
### Advantages and Disadvantages of Refactoring in General
In general, refactoring can be a very powerful tool and improve long and inefficient processes. There are a few obvious advantages to this. First, efficiency is always good when it comes to programs. If the program is long, it can significantly reduce the time it takes, and if the program is short, it might be reused or upscaled, at which point, more efficiency will have a multiplicatively more helpful. Another potential advantage for refactoring is to come up with creative solutions to problems, which can be used in future problems. Even if, again, the program is relatively short, the general idea of the solution can be used in future problems and programs. There are, however, disadvantages to refactoring. First, if the program is short, the increased efficienccy may only take seconds or tenths of seconds off of the total time it takes to run. This time can be negligible compared to the time it takes to come up with and inplement a more efficient process. This time could be used to work on other projects, or the next step of the same project.

### Advantages and Disadvantages of Refactoring This Code
When looking at this specific VBA script, it already runs fairly quickly. The original time, before refactoring, was under 1 second. So, even though it was not the cleanest way to get to a solution, it was clean enough, considering we were working with not very much data. The refactoring allowed the program to run about 4x faster, which is significant, at the amount of data we were using. However, there are still good reasons to refactor this code. If we wanted to scale this up to examine any significantly larger number of stocks, the refactored code will run exponentially faster. This is because the original code had for loops that consisted of the number of stocks and the number of rows in the sheet. Both of these will increase if we scale up the analysis, and since the loops were nested, the number of conditionals is related to their product. In the refactored analysis, there is only one for loop with just the number of rows in thes sheet. While this will, of course, take longer if the process is scaled up, it will only increase thenumber of conditionals by one factor. Finally, a disadvantage to refactoring this code is taht it relies on a specific formatting of the data sheet. If someone who does not understand this were to try to do additional analysis and change the data sheet such that it was sorted differently, it could mess up how this refactored program runs.
