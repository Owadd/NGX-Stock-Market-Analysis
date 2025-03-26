# Nigeria Stock Market Analysis (Jan - Feb 2025)

## Introduction
The Nigerian stock market is a vital indicator of the country’s economic strength and investor sentiment. This project provides an in-depth analysis of the Nigerian Exchange (NGX) performance from January to February 2025, highlighting key trends in market capitalization, sector performance, and top gainers and losers. The analysis utilizes data wrangling, Power BI visualizations, and DAX computations to extract meaningful insights.

## Problem Statement
Understanding stock market movements is essential for investors, policymakers, and analysts. This study aims to:
- Identify the **top companies by market capitalization** in February 2025.
- Determine the **best and worst-performing stocks** based on market cap changes.
- Analyze the **sectoral performance and market share** within NGX.
- Provide actionable insights through **data visualizations**.

## Tools Used
- **Microsoft Excel** (Data cleaning, transformations, and calculations)
- **Power Query** (Data extraction and preprocessing)
- **Power BI** (Data visualization and insights generation)
- **DAX** (Advanced calculations and measures)

## Skills Demonstrated
- **Data Cleaning & Preprocessing**
- **Data Analysis & Transformation**
- **Data Visualization & Reporting**
- **DAX Formulas & Measures**
- **Stock Market Trend Analysis**

## Data Preparation
### Initial Dataset in Power Query (Before Cleaning)
![Initial Dataset](path/to/initial_dataset.png)

### Data Cleaning Process
1. **Removed unnecessary columns** (e.g., Nominal Value, Shares Outstanding).
2. **Formatted column headers** for consistency.
3. **Converted data types** for accurate calculations.
4. **Merged January & February datasets** using XLOOKUP and TRIM.
5. **Computed percentage changes** in market capitalization.

### Cleaned Dataset (Final View in Excel)
![Cleaned Dataset](path/to/final_dataset.png)

## Data Visualization
### Sector Market Share (February 2025)
![Sector Market Share](path/to/sector_market_share.png)

### Company Performance Dashboard
![Power BI Dashboard](path/to/dashboard_image.png)

## Key Findings
### Top Companies by Market Cap (February 2025)
| Rank | Company | Market Cap (₦) |
|------|---------|----------------|
| 1    | AIRTEL Africa PLC | 8.11T |
| 2    | Dangote Cement PLC | 8.10T |
| 3    | BUA Foods PLC | 7.52T |
| 4    | MTN Nigeria Communications PLC | 5.55T |
| 5    | Seplat Energy PLC | 3.60T |

### Top Gainers (By % Market Cap Increase)
| Rank | Company | % Change |
|------|---------|-----------|
| 1    | Smart Products Nigeria PLC | +65% |
| 2    | PZ Cussons Nigeria  | +54% |
| 3    | UPDC PLC  | +53% |
| 4    | ETERNA PLC  | +52% |
| 5    | HONEYWELL FLOUR MILL PLC  | +43% |

### Worst Performing Companies (By % Market Cap Decrease)
| Rank | Company | % Change |
|------|---------|-----------|
| 1    | Union Dicon Salt Plc | -28% |
| 2    | Eunisell Interlinked Plc | -27% |
| 3    | Learn Africa Plc | -27% |
| 3    | University Press Plc | -19% |
| 3    | DAAR Communications Plc | -18% |

### Sector Performance (% Change in Market Cap)
| Rank | Sector                   | % Change in Market Cap |
|------|--------------------------|-----------------------|
| 1    | Construction/Real Estate | 153%                  |
| 2    | Consumer Goods          | 143%                  |
| 3    | Agriculture             | 88%                   |
| 4    | Industrial Goods        | 72%                   |
| 5    | Financial Services      | 59%                   |
| 6    | Oil And Gas            | 37%                   |
| 7    | Investment             | 18%                   |
| 8    | Conglomerates          | 18%                   |
| 9    | ICT                    | 14%                   |
| 10   | Utilities              | 4%                    |
| 11   | Healthcare             | 2%                    |
| 12   | Services               | 0%                    |
| 13   | Natural Resources      | -12%                  |

## DAX Measures Used
```DAX
Companies = 
VAR TotalCount = COUNTROWS('Full Sheet')
RETURN 
    IF(TotalCount > 1, TotalCount, TotalCount)

Overall Performance % = 
VAR MarketCapJan = SUM('Full Sheet'[Market Cap(Jan)])
VAR MarketCapFeb = SUM('Full Sheet'[MarketCap(Feb)])
RETURN 
    DIVIDE(MarketCapFeb - MarketCapJan, MarketCapJan, 0)

Total Market Cap (Feb) = SUM('Full Sheet'[MarketCap(Feb)])

MarketCap_Formatted = 
SWITCH(
    TRUE(),
    SUM('TopSectors'[Sum of MarketCap(Feb)]) >= 1000000000000, "₦" & FORMAT(SUM('TopSectors'[Sum of MarketCap(Feb)]) / 1000000000000, "0.00") & "T",
    SUM('TopSectors'[Sum of MarketCap(Feb)]) >= 1000000000, "₦" & FORMAT(SUM('TopSectors'[Sum of MarketCap(Feb)]) / 1000000000, "0.00") & "B",
    "₦" & FORMAT(SUM('TopSectors'[Sum of MarketCap(Feb)]), "0.00")
)

MarketCap_Sort = SUM('TopSectors'[Sum of MarketCap(Feb)])
```

## Insights
- **Banking and Telecoms sectors** were the biggest market movers.
- **Smart Products Nigeria PLC had the highest percentage gain**, while **Union Dicon Salt Plc suffered the largest loss**.
- **MTN Nigeria remained the dominant company** in terms of market capitalization.



### Author
**[Owadokun Oluwatobi Ezekiel]**  

This report showcases my expertise in **data analysis, Power BI reporting, and stock market insights**. By leveraging advanced data wrangling techniques, I have transformed raw data into a professional and impactful stock market analysis. 🚀
