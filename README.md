# time_series_analysis
time series---
==============
in common a time series is a sequence of values/numbers that are collected at successive 
equally spaced points.

more specifically, if we want to predict at time T which could be dependent on time at T-1,
T-2 and so on , then this series of data is known as a time series data.

time series and a non time series problem formulation are almost the same. then why do we 
have to treat it so differently?

taking a step back:-
==================== 
problems related to regression will have to use some points to learn and predict using other 
set of points. the case is same as in case of time series as well wherein we have some data points 
recorded at time intervals and all that we need to do is to learn and predict using a bunch of
time spaced data points.

in simple terms,using linear regression we are trying to find relation between one quantity and the 
other quantity, and so as time series very well tries to find relation between a lagged version of
time data points to present version of time data points. True.. 

Then why do we treat time series as fundamentally different from all other types of learning alrorithms?

For any given problem where our task is to predict for future using past inference can be formulated
into two types of problem- non time series and time series.

probelm:- 
=========
let us say you own a ice cream parlour. using past data you want to predict ice cream sales on any
given day? 

objective:-
===========
let us say you want to know what would be sales of ice cream tomorrow?

first approach:-
================
rationale:-
===========
using linear regression we have got the best fit of our line which will help us to predict. 
we can use of the below line of equation to predict by plugging any unseen data.temperature
on a a given day would be our input to the model as input feature.

linear regression hypotheis function-
=========================================
y = A0 + A1 * X1 + A2 * X2 + error....
y = A0 + A1*X + A2*X^2 + A3 * X^3 + error......


so using best fit of line and plugging in a date from date feature, you will get some prediction. 
accordingly for several other day you will get predictions as well. 

prediction will have some errors attached to it. using confidene interval we can estimate the 
proximity boundary meaning that how off we are expected to be. 

well,our errors for all observatons would be somewhat equally off, in the same band,meaning that 
it should not vary that much. the reason for this relates a point called interpolation. 

it means that we are using values from a certain range to predict , thus cerify our claim which uses 
a lot of values to train and predict from a range of values within, aka known range.

second approach:-
=================
rationale:-
===========
now let us look at the problem statement from the eye of time series learning algorithm.
our task is to create a function that predicts ice cream sales as on today Yt that depends 
upon Yt-1 and Yt-2 day sales. so temprature no longer would be fed to the model as an input, 
instead previous lagged values of ice cream sales would  be our variable.

time series hypotheis function:-
================================
Yt = A0 + A1 * Xt-1 + A2 * Xt-2 + error....(a 2nd/2lag order regressive model)
--note:- 2nd order as we are depending upon 2lags of previous data to predict--

so using our hypothesis function and pluggng in a future date that is not there in our known range
to predict is known as extrapolation. 

Essentially, that holds true as we are predicting someting that is outside our value range. 

Time series always take into account using extrapolation, because if we are interpolating then quite 
significantly we are just predicting the past that already happened. 

However, in case of time series we are not worried about last month sales to predict as we already 
predicted that before.

in essence what we want is to predict what would be my ice cream sales next month. true..

doing extrapolation stuff eventually makes life a bit difficult, because as and when we are plugging
in a new future day/month data to predict not within the range of known values, error will be increasing
to a large extent.

in addition to that, there is always an uncertainity of capturing lagged values of past to predict a new
data point and also in a way we are propagating the recent past observation and its uncertainity to predict
next data. And that is why time series prediction interval range can be way off then expected to be. 


auto regression---
==================
assumpions:-
-----------
in this scenario we will assume that the series data points with any of its lagged values
will have correlation.

definition:-
============
a ststistical model is auto regressive if it predicts future value based on past value.

another definition:-
====================
an extension to linear regression model that uses time based sequencing where there is 
some correlation between values that precede and succeed, known as lags(lagged values) 
that will predict future based on past.


example:-
=========
if i say temprature at this time is 38 degree and somehow you can predict temprature
after one hour then it is auto regressive.


ACF(auto correlation function):-
================================
ACF is nothing but a direct and indirect function which returns values of auto-correlation with its 
lagged values. It represents that how well present values of time series is related with its past values. 
We will use this to get number of lagged values to be used in modelling.





PACF(partial auto correlation function):-
=========================================
PACF is nothing but an indirect function which returns values of auto-correlation with 
its residuals that remains after removing effects from previous lagged values and hence
the name partial is added.

The reason being removing known variations before we found unknown hidden information if
any, could be very well captured in next lag so that we attain good correlation to keep
that feature useful in order to avoid multi-collinearily.


<Short introduction to time series>
