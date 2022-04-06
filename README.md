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


components of time series:-
===========================
time series analysis paves us the way to predict future using past. Prediction will be made using hidden
pattern and data behaviors. analyzing time series data will show trends in data to define underline patterns
or processes around.


major components include,
1- trend 
2- seasonality
3- cyclicity
4- irregularity or error

trend:-
========
time related data points tends to increase or decrease over time and over a long period this clearly
depicts the story or movement of data. not always trend will increase or decrease, also with change
in time trend can be stable as well. 

seasonality:-
=============
time related data points shows variation some variable in association with some predetermined behavior or
patterns. more often then not seasonality will be captured regularly in a specific time window space one after
another.

cyclicity:-
===========
time related data points shows more information about seasonality and its pattern. it can be explained by other cyclical
movements in data.

irreglarirt:-
=============
time related data points shows random behavior of any varible which can not be explained by cyclical movements.
in other terms this term gives non seasonal patterns in data.






stationarity:-
==============

a time series is a stationary time series if mean and variance between two consecutive
time interval remains constant. And there exists no seasonality in time series.

checking for stationarity:-
===========================
1- visual eyeballing
2- mathematical intuition (local tests)
3- hypotheis test of sinificance (adf test)

how to make a time series stationary:-
=====================================
suppose a time series is modelled by,
Yt = A0 + A1 * Yt-1 + Error...
Zt = Yt - Yt-1(as per definition)

fitting equation of time series,
Zt = A0 + A1 * Yt-1 + Error(t) - A0 - A1 * Yt-2 - Error(t-1)
Zt = A1 + Error(t-1) - Error(t-2)

So, mean of Zt would be a constant term and variance as well.


Now we can use Zt time series to build models and generate predictions. One thing to notice here 
is that Zt time series would contain one observation less than Yt,because we are taking two consecutive
observations to make it stationary.


augmented dickey fuller test:-
============================= 

well, initially we have looked at time series and derived local tests under certain 
time intervals to justify time series properties. on the whole these tests does not provide substantial
background of time series property. We as data practioners need to always proof something based upon statistical
tests and its significance. the answer to this is ADF test, a.k.a augmented dickey fuller test.

in this test we will try to build a robust process around time series to make more formal tests
on time series properties that are in question of stationarity?

performing dickey fuler test assumes that the given time series is a non stationary one.
Functionally the time series is a linear function of its one lag period in the past , 
a.k.a AR1 process.

Yt = Mean + Theta1 * Yt-1 + Error

The null hypothesis of dickey fuller test states that the given time series is a non-stationary one.
In contrast the alternate hypothesis states that the given time series is a stationary one.

the hypothesis test calculates p-value assuming that null to be true what is the probability
of getting an alternate hypothesis to be true more towards it. if p-value < 0.05 then null go,
else if p-value > 0.05 then null fly.

H0 (null hypothesis) => Theta1 = 1 (having unit root,non-stationary)
HA (alternate hypothesis) => Theta1 < 1 ( no unit root,stationary)


let us subtract Yt-1 from both sides of equation,
Yt-Yt-1 = Mean + (Theta1-1) * Yt-1 + Error
DeltaYt = Mean + Gamma * Yt-1 + Error

H0 (null hypothesis) => Gamma = 0 (non-stationary)
HA (alternate hypothesis) => Gamma < 0 (stationary)

we will use a dickey fuller distribution in this case to calculate p value.
ideally it should be t distribution in case of any regression prblem, but over here
Yt-1 is having a unit root which is why we go for a dickey fuller distribution.

formula for dickey fuller distribution- 
T-stats = gamma hat / std error(gamma hat)

now the question comes so naturally is that what if if we have time series that is a linear function
of previous all lagged values like AR 2,3,4 processes. That is where Augmented Dickey Fuller test comes
into the rescue. Just that we will extend the equation in turn making it more complicated.

composing this new version of augmented dickey fullrer test,
DeltaYt = Mean + Gamma * Yt-1  + SumOver(i=1 to P) Beta1 * Delta * Yt-1 + Error 
where Beta1 belongs to that dickey fuller distribution.
		

































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


let us take one scenario. we want to predict average monthly sales of fish.

deriving from time series, we know that measuremnt at time T would be dependent upon time T-1 and T-2.
We have taken 2nd order of time lag for the sake of simplicity , but choice is yours like T-3...., take 
how far you want to go with effect of time.

in order to determine sales of fish many factors come into play. For instance sales can be depedent upon
fishing regulation , other festivities around at that time and other local preferences. Among all these factors
the most intuitive thing that derives fish sales is last month sales price. Possibly a very good determiner.

Sales(T-2) can be related to Sales(T-1)-- direct
Sales(T-1) can be related to Sales(T)-- direct
Sales(T-2) can be related to sales(T)-- indirect, due to some eventuality

In this case, what ACF will do is to calculate auto correlation between Sales(T-2) and Sales(T).
It turns out that we are trying to find correlation between current month values with T-2 lagged
values. --Pearson correlation--

To be very precise, the transition from Sales(T-2) to Sales(T) would be comprised of direct and indirect
effects. Both of these effects would constitute basis of ACF function resulting in more lagged values.


PACF(partial auto correlation function):-
=========================================
PACF is nothing but an indirect function which returns values of auto-correlation with 
its residuals that remains after removing effects from previous lagged values and hence
the name partial is added.

The reason being removing known variations before we found unknown hidden information if
any, could be very well captured in next lag so that we attain good correlation to keep
that feature useful in order to avoid multi-collinearily.

Sales(T-2) can be related to sales(T)-- indirect, due to some eventuality

In this case, what PACF will do is to calculate auto correlation between Sales(T-2) and Sales(T-1).
It turns out that we are trying to find correlation between two lagged version of time series. This
will be helping us to find all possible lags and its dependencies after removing direct effects resulting
in less number of lagged values to avoid multicollnearity.
