# Generate-baseline-R-tools

A. Objective: generate forecast at SKU level, by any time horizon (by week, by month) automatically

B. Mechanism:

1. Data structure: N x M matrix.
	N is time horizon
	M are volume by ton of SKUs, exclude B2B

2. Forecast function: HoltWinters (HW), Seasonal Linear (SLN), ARIMA. Parameters of model are optimized automatically

3. Data pre-processing:
	if ( 3 years < historical data) : model read data from year 2015, use HW and SLN .
	
	if ( 2 years < historical data < 3 years) : model read data from year 2016, use HW and SLN .
	
	if ( 1 years < historical data < 2 years) : model read data from year 2017, use SLN .
	
	other : use ARIMA
	
4. Interate each SKU and generate forecast, then append them to one data frame.
