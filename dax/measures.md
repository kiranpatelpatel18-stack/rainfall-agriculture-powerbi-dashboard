Rainfall Measures :
Total_rainfall = SUM('rain-agriculture'[Total Rainfall])
Avg Rainfall = AVERAGE('rain-agriculture'[Total Rainfall])
Agriculture Measures:
Total Rice Area = SUM('rain-agriculture'[RICE AREA (1000 ha)])
Avg Rice Area = AVERAGE('rain-agriculture'[RICE AREA (1000 ha)])
Correlation Helper Measure: 
Rainfall per Area = DIVIDE([Total_rainfall], [Total Rice Area])
Rainfall YoY Growth = DIVIDE([Total_rainfall] - CALCULATE([Total_rainfall], PREVIOUSYEAR(DimYear[Year])), CALCULATE([Total_rainfall], PREVIOUSYEAR(DimYear[Year])))
