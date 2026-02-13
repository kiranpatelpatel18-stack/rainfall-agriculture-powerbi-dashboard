Created new table : DimYear = DISTINCT('rain-agriculture'[Year])
Created relationship → rain-agriculture[Year] → DimYear[Year]
Create Dimension: In Power Query, New Source > Blank Query > For State_Dim: = Table.Distinct(Table.SelectColumns(Agri_Rainfall_Data, {"State Name"})) – Rename table.
Created relationship: rain-agriculture[State Name] → State_Dim[State Name]
