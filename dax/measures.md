Rainfall Measures :
1. Total_rainfall = SUM('rain-agriculture'[Total Rainfall])
2. Avg Rainfall = AVERAGE('rain-agriculture'[Total Rainfall])
3. Agriculture Measures:
Total Rice Area = SUM('rain-agriculture'[RICE AREA (1000 ha)])
Avg Rice Area = AVERAGE('rain-agriculture'[RICE AREA (1000 ha)])
4. Correlation Helper Measure: 
Rainfall per Area = DIVIDE([Total_rainfall], [Total Rice Area])
Rainfall YoY Growth = DIVIDE([Total_rainfall] - CALCULATE([Total_rainfall], PREVIOUSYEAR(DimYear[Year])), CALCULATE([Total_rainfall], PREVIOUSYEAR(DimYear[Year])))
5. Correlation Rainfall vs Rice = 
VAR SummaryTable =
    SUMMARIZE(
        'rain-agriculture',
        'rain-agriculture'[Year],
        "Rain", [Total_rainfall],
        "Rice", [Total Rice Area]
    )

VAR AvgRain = AVERAGEX(SummaryTable, [Rain])
VAR AvgRice = AVERAGEX(SummaryTable, [Rice])

VAR Numerator =
    SUMX(
        SummaryTable,
        ([Rain] - AvgRain) * ([Rice] - AvgRice)
    )

VAR Denominator =
    SQRT(
        SUMX(SummaryTable, POWER([Rain] - AvgRain, 2)) *
        SUMX(SummaryTable, POWER([Rice] - AvgRice, 2))
    )

RETURN
    DIVIDE(Numerator, Denominator)
6. Correlation Interpretation = 
SWITCH(
    TRUE(),
    [Correlation Rainfall vs Rice] >= 0.7, "Strong Positive Relationship",
    [Correlation Rainfall vs Rice] >= 0.3, "Moderate Positive Relationship",
    [Correlation Rainfall vs Rice] > 0, "Weak Positive Relationship",
    [Correlation Rainfall vs Rice] = 0, "No Relationship",
    [Correlation Rainfall vs Rice] < 0, "Negative Relationship"
)
