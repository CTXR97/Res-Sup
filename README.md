# Resistance and Support Levels 

Resistance and Support Levels based on Candlesticks using Python

In theory, a fractal is a candlestick pattern made by 5 candles. The third candle has the lowest low price, the previous candles have decreasing lows and the next candles have increasing lows. By this pattern, the low of the third candle is the support level. The same concept applies to resistance levels, where the third candle has the highest high of the five ones. For this model, it was created in such a way that user can determine how many candles before and after the pivot to determine it as a support or resistance. 

![image](https://user-images.githubusercontent.com/107907500/177912191-18b8cc03-4d5d-4cf6-bc0e-15ad12d62873.png)

Therefore what the code aims to do is to identify these pivots and draw a support and resistance. The first graph will end up like this:

<img width="1139" alt="Screenshot 2022-07-11 at 8 51 33 PM" src="https://user-images.githubusercontent.com/107907500/178268311-7eacdf6c-0219-4f92-9a1b-307bb7f3bca5.png">

As there are many lines drawn and are pretty close to each other, part of the code will allow user to determine what is the user's comfortable range i.e difference between the 2 lines must be less than or equal to a certain value. Final results should be as follow:

![image](https://user-images.githubusercontent.com/107907500/178689473-06cfd79c-f900-4bf5-93f2-45d360785e8b.png)

The final output also includes the specific numbers:

<img width="283" alt="Screenshot 2022-07-11 at 8 50 46 PM" src="https://user-images.githubusercontent.com/107907500/178268178-ae6cfd51-8d2f-433a-b6d9-bcad07243428.png">

Things to note with this model:
1. The input data is very sensitive. As part of my backtest, I used the following:
  a. CSV file with 'dirty' numbers i.e values with commas.
  b. xslx file with clean numbers.
  c. xslx file with 'dirty' numbers.

2. Part of the code also includes the range of data to be tested. For example a data set with 262 days is expected to have 262 candles representing each day. However, user might choose a specific period to test for example day 0 to day 240 and this should be stated explicitly in the code. In addition, user have to take into account how many candle sticks before and after the pivot as the range for testing should exclude this number. For example, testing range 0 to 240, with 3 candlesticks before and 2 candlesticks after the pivot. The range should then be 3 to 238
