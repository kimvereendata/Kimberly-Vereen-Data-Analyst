🔗 Download Full Portfolio PDF (Hi-Res) [https://kimberlyvereendataportfolio.my.canva.site/42k](https://kimberlyvereendataportfolio.my.canva.site/42k)


# 🏨 Hotel Revenue Intelligence Dashboard – Le Meridien Focus

## 📊 Project Overview
This Power BI project explores regional hotel performance and customer behavior using a dataset sourced from Kaggle. The primary focus is on **Le Meridien in Sabah**, with comparative insights from other competing hotels in Malaysia. Forecasting, segmentation, and booking behavior analysis are used to drive actionable business recommendations for hotel management.

---

## 🧹 Data Preparation

1. **Source**: Dataset downloaded from Kaggle (Hotel Sales)
2. **Cleaning**: Handled nulls, renamed columns, and corrected formats using Excel
3. **Import**: Cleaned dataset imported into Power BI as a single table: `Hotels Data Clean`
4. **Modeling**:
   - Created calculated tables to support time intelligence and forecasting
   - Added date-related columns and marked a custom date table for accurate month/year sorting

---

## 📁 Dataset Overview

**Main Table**: `Hotels Data Clean`

**Key Columns:**

- **Hotel & Customer Info**: `hotel_name`, `hotel_type`, `region`, `state`, `customer_name`, `customer_segment`, `room_type`, `booking_channel`
- **Financials**: `price`, `nights`, `discount`, `disc_amt`, `sales`, `avg_daily_rate`
- **Dates**: `arrival_date`, `arrival_month`, `departure_month`

---
🎯 Key Project Objectives
📈 Objective 1: Forecast Monthly Revenue
Goal: Predict monthly room revenue trends at Le Meridien to support data-driven staff planning and strategic sales forecasting.

Implementation Steps:

Created a Date Table:
DateTable = 
CALENDAR(MIN('Hotels Data Clean'[arrival_date]), MAX('Hotels Data Clean'[departure_date]))

Added Time Intelligence Columns:
Year = YEAR('DateTable'[Date])
Month = FORMAT('DateTable'[Date], "MMMM")
MonthNumber = MONTH('DateTable'[Date])
YearMonth = FORMAT('DateTable'[Date], "YYYY-MM")

Marked the table as a Date Table and created a relationship to 'Hotels Data Clean'[arrival_date].

Created Sales Measure:
Total Sales = SUM('Hotels Data Clean'[sales])

Built Visual in Power BI:
Visual Type: Line Chart
X-Axis: DateTable[YearMonth]
Y-Axis: Total Sales
Forecasting: 12-month forecast added via the Analytics pane

🔍 Key Insight:
The Studio Room emerged as the top revenue generator, forecasting ~$520,948, while the Royal Suite lagged behind at ~$126,579.

👥 Objective 2: Predict Staffing Requirements from Booking Trends
Goal: Estimate monthly staffing needs based on booking volumes to enhance operational efficiency.

Implementation Steps:
Linked DateTable[Date] to 'Hotels Data Clean'[arrival_date].

Created Measures:
Total Bookings = COUNTROWS('Hotels Data Clean')
Estimated Staff Required = ROUNDUP([Total Bookings] / 5, 0)

Built Visual in Power BI:
Visual Type: Area Chart
X-Axis: DateTable[YearMonth] (sorted by MonthNumber)
Y-Axis: Estimated Staff Required
Slicers: room_type, hotel_name
Trend Line: Added to illustrate staffing fluctuations

🔍 Key Insight:
Studio Room bookings consistently peak in January, March, June, and September, requiring up to 43 staff members during these high-demand periods.

🧭 Objective 3: Segment Analysis for Targeted Marketing
Goal: Understand how different customer segments contribute to total sales across room types, to uncover high-value combinations for targeted campaigns.

Implementation Steps:

Created Sales Measure:
Total Sales = SUM('Hotels Data Clean'[sales])

Built Visual in Power BI:
Visual Type: Stacked Column Chart
X-Axis: customer_segment
Y-Axis: Total Sales
Legend: room_type
Slicers: booking_channel, region, room_type

🔍 Key Insight:
The Corporate segment generates over $6.5 million in sales, yet makes no purchases of the Royal Suite, suggesting a missed opportunity for luxury upselling within this high-yield group.

📦 Objective 4: Analyze Booking Channel Performance
Goal: Identify the most profitable booking channels and assess how discount strategies impact their performance, to optimize pricing and promotional tactics.

Implementation Steps:

Created Core Measures:
Total Nights = SUM('Hotels Data Clean'[nights])
Total Discount = SUM('Hotels Data Clean'[disc_amt])
Total Sales = SUM('Hotels Data Clean'[sales])

Built Visuals in Power BI:
Clustered Bar Chart
Y-Axis: MonthLabel
X-Axis: Total Nights
Legend: booking_channel
Stacked Area Chart
X-Axis: booking_channel
Y-Axis: Total Discount
Slicers: hotel_name and room_type
Supporting table analyzing customer_segment by total nights

🔍 Key Insight:
Booking.com drives the highest room-night revenue at $54K but also leads in discount costs, indicating revenue is discount-dependent. In contrast, Direct bookings generate fewer nights at $48K with significantly lower discounts at $45K suggesting an opportunity to boost this cost-efficient channel through targeted promotions.
