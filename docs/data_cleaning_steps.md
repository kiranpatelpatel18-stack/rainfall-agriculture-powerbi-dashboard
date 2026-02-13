Changed data types to:
State Name → Text
Year → Whole number
Rainfall months → Decimal
Rice Area → Decimal
Filtered each rainfall column → removed blanks
Renamed columns: RICE AREA (1000 ha) → Rice Area (kha), JUN → Rainfall Jun, JUL → Rainfall Jul
Added Custom Column: Total Rainfall = [Rainfall Jun] + [Rainfall Jul] + [Rainfall Aug] + [Rainfall Sep]
Removed duplicate column - 'Year.1'
Select State Name > Transform > Capitalize Each Word
Selected subdivision (seems redundant, e.g., "andhra pradesh") > Removed as its identical to State Name.
