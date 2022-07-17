# Resistance and Support Levels 

Resistance and Support Levels based on Candlesticks using Python

In theory, a fractal is a candlestick pattern made by 5 candles. The third candle has the lowest low price, the previous candles have decreasing lows and the next candles have increasing lows. By this pattern, the low of the third candle is the support level. The same concept applies to resistance levels, where the third candle has the highest high of the five ones. For this model, it was created in such a way that user can determine how many candles before and after the pivot to determine it as a support or resistance. 

![image](https://user-images.githubusercontent.com/107907500/177912191-18b8cc03-4d5d-4cf6-bc0e-15ad12d62873.png)

Therefore what the code aims to do is to identify these pivots and draw a support and resistance. The first graph will end up like this:

![image](https://user-images.githubusercontent.com/107907500/178862381-41ed4f22-30b9-40d2-921b-c396283d1aab.png)

As there are many lines drawn and are pretty close to each other, part of the code will allow user to determine what is the user's 'comfortable' range between two lines. 

**Version 1:** User can choose to compare the difference between support/resistance prices respectively i.e within their own list.

![image](https://user-images.githubusercontent.com/107907500/178868026-041ea18c-d65b-4c76-aa95-2bf6363b2de2.png)

**Version 2:** User can choose to compare the difference between ALL prices i.e the entire universe.

![image](https://user-images.githubusercontent.com/107907500/178868078-8c022a20-853c-4fb7-8a6e-8e0ca0a3c5a7.png)

**Question:** What is the difference between version 1 and 2?

**Answer:** The results will be different because the comparison is in sequential order: [i] - [i-1] <= 'x' where 'x' is user-defined. By comparing within a list and comparing the entire universe, the order is different leading to different [i] and [i-1] prices so the final support and resistance prices will also be different. 

Final results should be as follow:

![image](https://user-images.githubusercontent.com/107907500/178866554-8ae27a15-fe60-444e-ae4a-0204090cfb88.png)

The final output also includes the specific numbers:

![image](https://user-images.githubusercontent.com/107907500/178862422-3b7184fe-6014-4e2f-a69f-e3dc072223e6.png)

***EDITED***
Added a new structure to populate the trend lines. It works as such: By identifying position x and determining the backtest range as well as the intervals. Within each interval, to determine the high and low points

<img width="343" alt="Screenshot 2022-07-17 at 1 28 35 PM" src="https://user-images.githubusercontent.com/107907500/179385238-aa95ee52-a73f-46e4-9da4-975eeb5f0df9.png">

Once this is determined, the codes will plot a best fit line through all the lows and highs respectively. 
However, this is still not very accurate therefore, the strategy is to do the following:

1. To find the difference between the plotted slope as well as the identified high or low and readjust the trend line.
2. After which, there could still be high and lows above the readjusted trend line, so the code takes into account this issue and does another readjustment. 

The final graph will end up like this:

<img width="1175" alt="Screenshot 2022-07-17 at 1 33 46 PM" src="https://user-images.githubusercontent.com/107907500/179385323-787b3cd2-3255-411c-9802-9d7b2e00d9a8.png">

Things to note with this model:
1. The input data is very sensitive. As part of my backtest, I used the following:
  a. CSV file with 'dirty' numbers i.e values with commas.
  b. CSV with clean numbers
  c. xslx file with clean numbers.
  d. xslx file with 'dirty' numbers.
 
Results show that some modification/cleaning up of the data is required to fit the code structure. By default, I used **TTFG1MON SPEC Index** from bloomberg as the default file hence the codes will take it as the base. (Assuming in the future all data is drawn from bloomberg, I do not foresee any issues with this)

![image](https://user-images.githubusercontent.com/107907500/178708618-d41c5440-1608-473f-8c1f-0e3e7c920b55.png)

As seen from the codes, I tested on HSI as well (dirty data) and few modifications required. In such a scenario, just remove the '#' and add '#' to those irrelevant codes to run them. '#' means to change it to a text form so python will skip them. 

2. Part of the code also requires user to define the range of data to be tested based on the data input the user has chosen 

3. For the trend lines, it is unable to take into account abnormality. For example, a sudden spike in prices might show a very huge range between support and resistance and by right, it is not recommended to trade within the huge range. This model is unable to take into account such issues and do a readjustment of the trend lines accordingly. 

4. In addition to point3, the model also plots the trend lines of the specific range specified by the user. If we plot the trend lines of the entire dataset, it will show the general direction. In short, this model can be considered to be 'one-dimensional' i.e only one direction available at each time. As of now, I am unable to do a 'multi-directional' model. 

In theory to build a multi-dimensional model, the steps are:

1. Find all local minimas and maximas
2. Draw lines between all of them
3. Eliminate non trend lines
4. Combine similiar trend lines
5. Rate each trend lines by strength
6. Eliminate weak lines 
