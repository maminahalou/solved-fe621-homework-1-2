Download Link: https://assignmentchef.com/product/solved-fe621-homework-1-2
<br>
For all the problems in this assignment you need to design and use a computer program, output results and present the results in nicely formatted tables and figures. The computer program may be written in any programming language you want. Please write comments to all the parts of your code

Part 1.  Data gathering component

1.       Write a function (program) to connect to sources and download data from one of the following sources:

(a)    GOOGLE finance http://www.google.com/finance

(b)    Yahoo Finance http://finance.yahoo.com

(c)    Bloomberg

Notes. For extra credit you can turn in code to download data from the other two sources. Please note that the program needs to download both option data and equity data. For this problem (and only for this problem) you may use any built in function or toolbox that will facilitate your work. The data will have to be clean (no duplicated values, only one exchange, every column labeled properly, in other words consolidated).

Note on Bloomberg data. For the Bloomberg source access to one of Bloomberg terminals in the lab is required. If you use Bloomberg data you may use the API to download data in Excel automatically and organize the data. However this should be accomplished with an automatic script. If you use R to interface with the Bloomberg data an useful package is Rblpapi, but there are other packages. For the online students who do not have access to Bloomberg terminals to download yahoo and google data automatically you may read about the package quantmod available in R.

Bonus Create a program that is capable of downloading multiple assets combine them with the associated time column and save the data into a csv or excel file.

2.       With the function created in problem 1. download data on both options and equity for the following symbols:

•    AMZN

•    SPY

•    VIX

for two consecutive days (does not matter when but no later than February 8th) during the trading day (9:30am to 4:00pm). Please record the asset values (both AMZN and SPY) at the time when downloading is done. Please do the same with the VIX. For the options please download the next maturities data. Please note that the traditional options are maturing third Friday on the month but there are a lot more options available to download. To be specific you should download at least all the option chains until the ones maturing two and three months from the date you are downloading.

We shall refer to the data sets gathered in the two consecutive days as DATA1 (for the first day) and DATA2 (for the second day) respectively throughout this assignment and the following ones.

3.       Write a paragraph describing the symbols you are downloading data for. Explain what is the SPY and its purpose. (Hint: look up the definition of an ETF). Explain what is VIX and its purpose. Understand the options symbols. Understand when each option expires. Write this information and turn it in.

4.       The following items will also need to be recorded:

•    The underlying equity or ETF price at the exact moment when the rest of the data is downloaded.

•    The short-term interest rate which may be obtained here:

http://www.federalreserve.gov/releases/H15/Current/. There are a lot of rates posted on the site – they are all yearly, they are in percents and need to be converted to numbers. There is no theoretical recommendation on which to use, I used to use 3-months Treasury bills which are not available anymore. Since then I have been using the “Federal funds (effective)” rate but you can go ahead and try others. You should remember to be consistent in your choice. Also, make sure that the interest rate that you use is for the same day when the data you use for the implied volatility was gathered and note that the data is typically quoted in percents (you will need numbers). The same site has a link to past

(historical) interest rates.

•    Time to Maturity.

Part 2. Analysis of the data.

5.       Using your choice of computer programming language implement the Black-Scholes formulas as a function of current stock price S0, volatility σ, time to expiration T − t (in years), strike price K and short-term interest rate r (annual). Please note that no toolbox function is allowed but you may use the normal CDF calculation.

6.       Implement the Bisection method to find the root of arbitrary functions. Apply this method to calculate the implied volatility on the first day you downloaded (DATA1). For this purpose use as the option value the average of bid and ask price if they both exist (and if their corresponding volume is nonzero). Also use a tolerance level of 10−6. Report the implied volatility at the money (for the option with strike price closest to the traded stock price). You need to do it for both the stock and the ETF data you have (you do not need to do this for VIX). Then average all the implied volatilities for the options between in-the-money and out-of-the-money.

Note. There is no clearly defined boundary between options at-themoney and out-of-the-money or in-the-money options. If we define moneyness as the ratio between S0 the stock price today and K the strike price of the option some people use values of moneyness between 0.95 and 1.05 to define the options at the money. Yet, other authors use between 0.9 and 1.1. Use these guidelines if you wish to determine which options’ implied volatilities should be averaged.

7.       Implement the Newton method/Secant method or Muller method to find the root of arbitrary functions. You will need to discover the formula for the option’s derivative with respect to the volatility σ. Apply these methods to the same options as in the previous problem. Compare the time it takes to get the root with the same level of accuracy.

8.       Present a table reporting the implied volatility values obtained for every maturity, option type and stock. Also compile the average volatilities as described in the previous point. Comment on the observed difference in values obtained for AMZN and SPY. Compare with the current value of the VIX. Comment on what happens when the maturity increases. Comment on what happen when the options become in the money respectively out of the money.

9.       For each option in your table calculate the price of the different type (Call/Put) using the Put-Call parity (please see Section 4 from [2]). Compare the resulting values with the BID/ASK values for the corresponding option if they exist.

10.   Consider the implied volatility values obtained in the previous parts. Create a 2 dimensional plot of implied volatilities versus strike K for the closest to maturity options. What do you observe? Plot all implied volatilities for the three different maturities on the same plot, where you use a different color for each maturity. In total there should be 3 sets of points plotted with different color. (BONUS) Create a 3D plot of the same implied vols as a function of both maturity and strike, i.e.: σ(τi,Kj) where i = 1,2,3, and j = 1,2,…,20.

11.   (Greeks) Calculate the derivatives of the call option price with respect to S (Delta), and σ (Vega) and the second derivative with respect to S (Gamma). First use the Black Scholes formula then approximate these derivatives using an approximation of the partial derivatives. Compare the numbers obtained by the two methods. Output a table containing all derivatives thus calculated.

12.   Next we will use the second dataset DATA2. For each strike price in the data use the Stock price for the same day, the implied volatility you calculated from DATA1 and the current short-term interest rate (corresponding to the day on which DATA2 was gathered). Use the Black-Scholes formula, to calculate the option price.

Part 3. Numerical Integration of real-valued functions.

Consider the real–valued function

, for x 6= 0, for x = 0.

Note that we can actually calculate this integral as:  .

1.    Implement the trapezoidal and the Simpson’s quadrature rules to numerically approximate the indefinite integral above. The algorithms are presented in [3], please see Chapter 5. Hint: you can approximate the indefinite integral by considering a large interval [−a,+a] (for example a = 106). Consider equidistant nodes , i.e.,  0,1,…,N, where N is a large integer.

2.    Compute the truncation error for the numerical algorithms implemented in 1 for a particular a ∈ R and N ∈ N. That is, create a function of a and N that will output IN − π, where IN,a is the numerical approximation of the integral. Study the changes in the approximation as N and a increase as well as the difference between the two quadrature approximations. Please write your observations.

3.    In a typical scenario we do not know the true value of the integral. Thus, to ensure the convergence of the numerical algorithms we pick a small tolerance value ε and we check at every iteration k = 1,2,… if the following condition holds:

|Ik − Ik−1| &lt; ε,

where Ik is the value of the integral at step k. When the condition holds, the algorithm stops. Evaluate the number of steps until the algorithms from a) reach convergence for ε = 10−4. What do you observe?

4.    Consider

g(x) = 1 + e−x2 cos(8×2/3).

Use the trapezoidal rule and Simpson’s rule to approximate  . Use a tolerance level of ε = 10−4.