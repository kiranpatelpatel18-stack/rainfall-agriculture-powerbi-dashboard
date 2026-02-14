Created new table : DimYear = DISTINCT('rain-agriculture'[Year])
Created relationship → rain-agriculture[Year] → DimYear[Year]
Create New Table: State_Dim = DISTINCT('rain-agriculture'[State Name])
Created relationship: rain-agriculture[State Name] → State_Dim[State Name]
