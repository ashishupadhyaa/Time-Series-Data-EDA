# Time-Series-EDA
<ins>EDA of time-series data</ins>

In this project, i explore the data which have a column of **Date-Time** and also predict some future values using models as *Moving Average*, *Exponential Smoothing*, *Double Exponential Smoothing*, *Triple Exponential Smoothing*, *LinearRegression* and *XGBRegressor*.

**Moving Average** :-
In this, we will assume that the future value of our variable depends on the average of its *k* previous values. Therefore, we will use the moving average.

&ycirc;<sub>t</sub> = (1 / k) &sum;<sub>n=1 to k</sub> y<sub>t-n</sub>

**Exponential Smoothing** :-
Here the model value is a weighted average between the current true value and the previous model values. The &alpha; weight is called a smoothing factor. It defines how quickly we will *"forget"* the last available true observation. The smaller &alpha; is, the more influence the previous observations have and the smoother the series is.
Exponentiality is hidden in the recursiveness of the function, we multiply by (1-&alpha;) each time, which already contains a multiplication by (1-&alpha;) of previous model values.

&ycirc;<sub>t</sub> = &alpha; . y<sub>t</sub> + (1 - &alpha;) . &ycirc;<sub>t-1</sub>

**Double Exponential Smoothing** :-
Series decomposition will help us -- we obtain two components: intercept (i.e. level) $\ell$ and slope (i.e. trend) $b$.

&ell;<sub>x</sub> = &alpha;y<sub>x</sub> + (1 - &alpha;)(&ell;<sub>x-1</sub> + b<sub>x-1</sub>)

b<sub>x</sub> = &beta;(&ell;<sub>x</sub> - &ell;<sub>x-1</sub>) + (1 - &beta;)b<sub>x-1</sub>

&ycirc;<sub>x+1</sub> = &ell;<sub>x</sub> + b<sub>x</sub>

The first one describes the intercept, which, as before, depends on the current value of the series. The second term is now split into previous values of the level and of the trend. The second function describes the trend, which depends on the level changes at the current step and on the previous value of the trend. In this case, the $\beta$ coefficient is a weight for exponential smoothing. The final prediction is the sum of the model values of the intercept and trend.

**Triple Exponential Smoothing (HoltWinters)** :-
In this, seasonality. This means that we should not use this method if our time series is not expected to have seasonality. Seasonal components in the model will explain repeated variations around intercept and trend, and it will be specified by the length of the season, in other words by the period after which the variations repeat. For each observation in the season, there is a separate component; for example, if the length of the season is 7 days (a weekly seasonality), we will have 7 seasonal components, one for each day of the week.

&ell;<sub>x</sub> = &alpha;(y<sub>x</sub> - s<sub>x-L</sub>) + (1 - &alpha;)(&ell;<sub>x-1</sub> + b<sub>x-1</sub>)

b<sub>x</sub> = &beta;(&ell<sub>x</sub> - &ell;<sub>x-1</sub>) + (1 - &beta;)b<sub>x-1</sub>

s<sub>x</sub> = &gamma;(y<sub>x</sub> - &ell;<sub>x</sub>) + (1 - &gamma;)s<sub>x-L</sub>

&ycirc;<sub>x+m</sub> = &ell;<sub>x</sub> + mb<sub>x</sub> + s<sub>x-L+1+(m-1)*mod*L</sub>

**Linear Regression** :-
The Plot of the result of the *LinearRegression* model is as follows-

[!alt text](/images/lr.png "Linear Regression model plot")

**XGBRegressor** :-
The Plot of the result of the *XGBRegressor* model is as follows-

[!alt text](/images/xgr.png "XGBRegressor model plot")

### The End
