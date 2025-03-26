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
| 1    | MTN Nigeria Communications PLC | 5.25T |
| 2    | Zenith Bank PLC | 1.59T |
| 3    | United Bank for Africa PLC | 1.29T |

**_Image Placeholder: Top Companies Chart_**  
`![Top Companies](path/to/top_companies.png)`

### Top Gainers (By % Market Cap Increase)

| Rank | Company | % Change |
|------|---------|-----------|
| 1    | XYZ Corp | +45% |
| 2    | ABC Ltd  | +38% |
| 3    | LMN Inc  | +32% |

**_Image Placeholder: Top Gainers Chart_**  
`![Top Gainers](path/to/top_gainers.png)`

### Worst Performing Companies (By % Market Cap Decrease)

| Rank | Company | % Change |
|------|---------|-----------|
| 1    | DEF Plc | -28% |
| 2    | GHI Ltd | -22% |
| 3    | JKL Inc | -19% |

**_Image Placeholder: Worst Performers Chart_**  
`![Worst Performers](path/to/worst_performers.png)`

### Best Performing Sectors (By Market Cap Growth)

| Rank | Sector | % Change |
|------|--------|-----------|
| 1    | Banking | +27% |
| 2    | Telecoms | +22% |
| 3    | Manufacturing | +15% |

### Sector Market Share

| Sector | Market Share (%) |
|--------|------------------|
| Banking | 40% |
| Telecoms | 35% |
| Oil & Gas | 15% |

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
