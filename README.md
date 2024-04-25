# World-Energy-Consumption

The project's goal is to create an infographic of the consumption of renewable energy across the world. It aims to inform the public and possible areas of innovation for public and private stakeholders.

## Tools

### Power BI

- Loading and transforming the data in Power Query
- Data Modeling
- Creating a date table
- Calculating explicit measures in DAX
- Time Intelligence in DAX
- Data visualization

## Data

[World Energy Consumption Dataset]

The dataset includes information on the following:
- 7 continents
- Different energy sources and their demand, consumption, share to electricity generation, and greenhouse gas emissions.

  
## Data Exploration using Power Query

Once the data is loaded, the following steps are done:
- Choose relevant columns only (e.g., hydro, nuclear, solar, and wind).
- Check for the column quality and column profile.
- Handle missing values.
- Correct the data type.
- Create a date table.

## Generate KPIs using DAX

In the Measure Table, create the following measures:

- Total greenhouse gas emissions

 ```
Total Greenhouse Emissions = 
SUM(Energy[greenhouse_gas_emissions])
```

- Total consumption

```
Total Nuclear Consumption = 
SUM(Energy[nuclear_consumption])
```
  
- Consumption for the latest year

```
Latest Nuclear Consumption = 
LASTNONBLANK(
    Energy[nuclear_consumption],
    [Total Nuclear Consumption])
```

- Share for the latest year

```
Latest Nuclear Share = 
DIVIDE(
    LASTNONBLANK(
    Energy[nuclear_share_elec],
    [Nuclear Share]),
    100,
    "NA")
```

- Consumption for the Previous Year

```
Prev Nuclear Consumption = 
CALCULATE(
    [Total Nuclear Consumption],
    SAMEPERIODLASTYEAR('Date'[Date])
)
```

Note: Create the same measure for hydro, solar, and wind power.


## Dashboard

[View the dashboard here](https://app.powerbi.com/reportEmbed?reportId=5abb54f8-0a28-4872-b7b5-3062c5053f9e&autoAuth=true&ctid=e93c0c9e-286e-4c79-b4cd-be2a9d8ccf16)
