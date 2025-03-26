# Nigeria Stock Market Analysis (Jan - Feb 2025)

## Overview
This project analyzes the performance of Nigeria's stock market between January and February 2025 using data from the Nigerian Exchange (NGX). The analysis focuses on market capitalization, sector performance, and top gainers/losers.

## Data Sources
- **NGX Reports**: Downloaded from the NGX website
  - **SHARES OUTSTANDING FOR 31-01-2025** (January report)
  - **SHARES OUTSTANDING FOR 28-02-2025** (February report)
- **Sector Data**: Extracted from an internal NGX analysis file

## Objectives
- Identify the **top companies by market cap** in February
- Identify **companies with the least market cap**
- Determine the **top gainers and losers** from January to February
- Analyze the **best and worst performing sectors**
- Compute each **sector's share of the total market cap**

## Data Preparation
1. **Extracted data from PDF reports into Excel** using Power Query.
2. **Cleaned the data**:
   - Removed unnecessary columns (e.g., Nominal Value, Shares Outstanding)
   - Converted columns to appropriate data types
   - Handled missing values using data imputation
3. **Merged January & February data** into a unified table using XLOOKUP and TRIM.
4. **Computed percentage changes** in market cap and closing prices.
5. **Used Pivot Tables** for sector and company performance analysis.

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


### Best Performing Sectors (By Market Cap Growth)

### Sector Performance (% Change in Market Cap)

### Sector-wise % Change in Market Capitalization

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



### Sector Market Share

### Sector Market Capitalization (February 2025)

| Rank | Sector                   | Market Cap (NGN)           | Market Share (%) |
|------|--------------------------|---------------------------|------------------|
| 1    | ICT                      | 13,747,454,685,716        | 21.6%            |
| 2    | Industrial Goods         | 12,841,626,535,794        | 20.2%            |
| 3    | Financial Services       | 11,912,958,308,314        | 18.7%            |
| 4    | Consumer Goods           | 11,685,867,393,974        | 18.4%            |
| 5    | Oil And Gas              | 7,006,242,470,848         | 11.0%            |
| 6    | Utilities                | 5,611,750,000,000         | 8.8%             |
| 7    | Services                 | 1,593,969,450,966         | 2.5%             |
| 8    | Agriculture              | 1,342,886,063,397         | 2.1%             |
| 9    | Conglomerates            | 805,474,222,312           | 1.3%             |
| 10   | Construction/Real Estate | 434,830,693,834           | 0.7%             |
| 11   | Healthcare               | 127,058,555,591           | 0.2%             |
| 12   | Investment               | 66,382,892,840            | 0.1%             |
| 13   | Natural Resources        | 25,441,434,199            | 0.0%             |



**_Image Placeholder: Sector Market Share Pie Chart_**  
`![Sector Market Share](path/to/sector_market_share.png)`

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

## Conclusion
- **Banking and Telecoms sectors** were the biggest market movers
- **XYZ Corp had the highest % gain**, while **DEF Plc had the biggest loss**
- **MTN Nigeria remained the dominant company** in terms of market capitalization

## Future Improvements
- Automate data extraction using **Python & PDF parsing libraries**
- Enhance visualization using **Power BI & Tableau**
- Expand analysis to **quarterly and yearly trends**

---

### Author
**[Owadokun Oluwatobi Ezekiel]**  
