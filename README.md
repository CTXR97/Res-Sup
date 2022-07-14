# Resistance and Support Levels 

Resistance and Support Levels based on Candlesticks using Python

In theory, a fractal is a candlestick pattern made by 5 candles. The third candle has the lowest low price, the previous candles have decreasing lows and the next candles have increasing lows. By this pattern, the low of the third candle is the support level. The same concept applies to resistance levels, where the third candle has the highest high of the five ones. For this model, it was created in such a way that user can determine how many candles before and after the pivot to determine it as a support or resistance. 

![image](https://user-images.githubusercontent.com/107907500/177912191-18b8cc03-4d5d-4cf6-bc0e-15ad12d62873.png)

Therefore what the code aims to do is to identify these pivots and draw a support and resistance. The first graph will end up like this:

![image](https://user-images.githubusercontent.com/107907500/178689620-3f647769-592d-4acf-a2d3-e3ff52b82c69.png)

As there are many lines drawn and are pretty close to each other, part of the code will allow user to determine what is the user's 'comfortable' range between two lines. The limitation for this is that it does NOT provide a cross reference i.e user can only determine the 'comfortable' range between two prices within the list of support prices and list of resistance prices. This is because the support and resistance prices are stored in two separate lists hence unable to do a cross comparison. In addition, it is also notable that the comparison of prices within the list of support or resistance prices is in sequential order.

**Potential Question:** Can we store everything in one list and do the comparison?\n
**Answer:** Yes we can, but the final output will just be one list of data because we will be unable to differentiate which prices are support and/or resistance. 

**Potential Question:** If store everything in on list and do the comparison, is there difference in results?\n
**Answer:** Yes this is because we are now comparing all values so when [i] - [i-1], its a different [i] and [i-1] as compared to when we are looking at individual lists. 

![image](https://user-images.githubusercontent.com/107907500/178859003-f65b1819-e082-48e6-babe-70ed5d1b24af.png)

Final results should be as follow:

![image](https://user-images.githubusercontent.com/107907500/178689473-06cfd79c-f900-4bf5-93f2-45d360785e8b.png)

The final output also includes the specific numbers:

<img width="283" alt="Screenshot 2022-07-11 at 8 50 46 PM" src="https://user-images.githubusercontent.com/107907500/178268178-ae6cfd51-8d2f-433a-b6d9-bcad07243428.png">

Things to note with this model:
1. The input data is very sensitive. As part of my backtest, I used the following:
  a. CSV file with 'dirty' numbers i.e values with commas.
  b. CSV with clean numbers
  c. xslx file with clean numbers.
  d. xslx file with 'dirty' numbers.
 
Results show that some modification/cleaning up of the data is required to fit the code structure. By default, I used **TTFG1MON SPEC Index** from bloomberg as the default file hence the codes will take it as the base. (Assuming in the future all data is drawn from bloomberg, I do not foresee any issues with this)

![image](https://user-images.githubusercontent.com/107907500/178708618-d41c5440-1608-473f-8c1f-0e3e7c920b55.png)

As seen from the codes, I tested on HSI as well (dirty data) and few modifications required. In such a scenario, just remove the '#' and add '#' to those irrelevant codes to run them. '#' means to change it to a text form so python will skip them. 

2. Part of the code also includes the range of data to be tested. For example a data set with 262 days is expected to have 262 candles representing each day. However, user might choose a specific period to test for example day 0 to day 240 and this should be stated explicitly in the code. In addition, user have to take into account how many candle sticks before and after the pivot as the range for testing should exclude this number. For example, testing range 0 to 240, with 3 candlesticks before and 2 candlesticks after the pivot. The range should then be 3 to 238. 

3. Another limitation of this model is that; 
![image](https://user-images.githubusercontent.com/107907500/178861641-c7c43781-5146-4c06-b862-e6e32dae2378.png)

The image above was supposedly my expected graph so that we can actually see where is the support/resistance price drawn from. However, in order to do this graph, it needs to be done by indexing but during the comparison between prices as mentioned earlier, this unique key (in this case is the row number) is removed in order to calculate the difference in prices. I tried adding the row number back after the comparison but doesn't seem to work. In my opinion, this shouldn't be much of an issue because it is a display limitation, user is expected to refer to the summary table instead for the specific prices. 

