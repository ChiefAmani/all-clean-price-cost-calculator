# TECHNICAL_SPEC.md - Profit Per Job Calculator

## 1. Project Name
Profit Per Job Calculator

## 2. File Tree
.
|-- TECHNICAL_SPEC.md
|-- profit_per_job_calculator.xlsx

## 3. Tech Stack
Microsoft Excel (Version 2016 or newer recommended for full feature compatibility)

## 4. Excel Workbook Structure: profit_per_job_calculator.xlsx

The workbook will consist of several interconnected sheets, each serving a specific function to calculate profitability, track costs, and aid in pricing strategy.

### 4.1. Sheet: Dashboard Summary
*   **Purpose:** Provides a high-level overview of key financial metrics and profitability indicators.
*   **Key Outputs:**
    *   Average Profit per Job
    *   Total Monthly Profit (Estimated)
    *   Break-Even Number of Jobs
*   **Formulas (Referencing other sheets):**
    *   Average Profit per Job: = 'Job Costing'!B21 (Example cell reference)
    *   Total Monthly Profit (Est): = (Dashboard!B3 * Dashboard!B2) - 'Overhead & Break-Even'!B8 (Example cell references)
    *   Break-Even Number of Jobs: = 'Overhead & Break-Even'!B10 (Example cell reference)

### 4.2. Sheet: Job Costing
*   **Purpose:** Calculates the direct costs and profitability of an individual job, including labor, chemicals, and callback impacts.
*   **Key Inputs:**
    *   Total Job Price (Revenue)
    *   Estimated Labor Hours
    *   Hourly Labor Rate
    *   Other Direct Costs (e.g., consumables, specific materials)
    *   Estimated Callback Hours
    *   Callback Hourly Rate
    *   Callback Material Cost
    *   Total Chemical Cost
*   **Key Outputs:**
    *   Total Labor Cost
    *   Total Callback Cost
    *   Total Direct Job Cost
    *   Gross Profit per Job
    *   Gross Profit Margin (%)
*   **Formulas:**
    *   Total Labor Cost: = [Estimated Labor Hours] * [Hourly Labor Rate]
    *   Total Callback Cost: = ([Estimated Callback Hours] * [Callback Hourly Rate]) + [Callback Material Cost]
    *   Total Direct Job Cost: = [Total Labor Cost] + [Total Chemical Cost] + [Other Direct Costs] + [Total Callback Cost]
    *   Gross Profit per Job: = [Total Job Price] - [Total Direct Job Cost]
    *   Gross Profit Margin (%): = IF([Total Job Price] > 0, [Gross Profit per Job] / [Total Job Price], 0)

### 4.3. Sheet: Overhead & Break-Even
*   **Purpose:** Determines the number of jobs and revenue required to cover all fixed and variable overhead costs.
*   **Key Inputs:**
    *   Monthly Fixed Costs (e.g., rent, insurance, software subscriptions)
    *   Monthly Variable Overhead (e.g., office supplies, marketing spend)
    *   Average Direct Cost per Job (linked from Job Costing or user input)
    *   Average Revenue per Job (linked from Job Costing or user input)
*   **Key Outputs:**
    *   Total Monthly Overhead
    *   Contribution Margin per Job
    *   Break-Even Number of Jobs
    *   Break-Even Revenue
*   **Formulas:**
    *   Total Monthly Overhead: = [Monthly Fixed Costs] + [Monthly Variable Overhead]
    *   Contribution Margin per Job: = [Average Revenue per Job] - [Average Direct Cost per Job]
    *   Break-Even Number of Jobs: = IF([Contribution Margin per Job] > 0, [Total Monthly Overhead] / [Contribution Margin per Job], 0)
    *   Break-Even Revenue: = [Break-Even Number of Jobs] * [Average Revenue per Job]

### 4.4. Sheet: Pricing Strategy
*   **Purpose:** Helps determine if current pricing meets desired margins and generates "Good/Better/Best" pricing tiers. Includes the "Are You Undercharging" calculator.
*   **Key Inputs:**
    *   Desired Profit Margin (%)
    *   Total Estimated Job Cost (linked from Job Costing)
    *   Base Price for Good Tier
    *   Markup % for Better Tier
    *   Markup % for Best Tier
*   **Key Outputs:**
    *   Suggested Minimum Profitable Price
    *   Good Tier Price
    *   Better Tier Price
    *   Best Tier Price
*   **Formulas:**
    *   Suggested Min Profitable Price: = [Total Estimated Job Cost] / (1 - [Desired Profit Margin])
    *   Good Tier Price: = [Base Price for Good Tier]
    *   Better Tier Price: = [Base Price for Good Tier] * (1 + [Markup % for Better Tier])
    *   Best Tier Price: = [Base Price for Good Tier] * (1 + [Markup % for Best Tier])

### 4.5. Sheet: Equipment ROI
*   **Purpose:** Calculates the return on investment for new equipment purchases.
*   **Key Inputs:**
    *   Purchase Price
    *   Estimated Lifespan (Years)
    *   Estimated Maintenance Cost (Annual)
    *   Estimated Revenue Increase/Cost Savings per Job
    *   Average Jobs per Month
*   **Key Outputs:**
    *   Monthly Depreciation
    *   Total Annual Cost of Equipment
    *   Jobs to Break Even (ROI)
    *   Time to Break Even (Months)
*   **Formulas:**
    *   Monthly Depreciation: = [Purchase Price] / ([Estimated Lifespan] * 12)
    *   Total Annual Cost of Equipment: = ([Purchase Price] / [Estimated Lifespan]) + [Estimated Maintenance Cost]
    *   Jobs to Break Even (ROI): = IF([Est Revenue Increase/Cost Savings per Job] > 0, [Purchase Price] / [Est Revenue Increase/Cost Savings per Job], 0)
    *   Time to Break Even (Months): = IF([Average Jobs per Month] > 0, [Jobs to Break Even (ROI)] / [Average Jobs per Month], 0)

### 4.6. Sheet: Employee Compensation
*   **Purpose:** Calculates total labor costs including base pay, commissions, and bonuses.
*   **Key Inputs:**
    *   Base Hourly Rate
    *   Commission Rate (%)
    *   Performance Bonus Criteria ($)
    *   Job-specific Revenue (linked from Job Costing)
    *   Estimated Labor Hours (linked from Job Costing)
*   **Key Outputs:**
    *   Total Labor Cost per Job
    *   Net Profit after Employee Compensation
*   **Formulas:**
    *   Total Labor Cost per Job: = ([Estimated Labor Hours] * [Base Hourly Rate]) + ([Job-specific Revenue] * [Commission Rate]) + [Performance Bonus Criteria]
    *   Net Profit after Employee Comp: = [Job-specific Revenue] - [Total Labor Cost per Job] - 'Job Costing'!B15 - 'Job Costing'!B7 (Example cell references for Total Direct Job Cost and Total Chemical Cost)

### 4.7. Sheet: Drive Time & Setup Allocation
*   **Purpose:** Factors unbillable time (drive time, setup/teardown) into the job cost.
*   **Key Inputs:**
    *   Average Drive Time per Job (minutes)
    *   Average Setup/Teardown Time per Job (minutes)
    *   Hourly Rate for Unbillable Time
*   **Key Outputs:**
    *   Total Unbillable Time Cost per Job
    *   Recommended Adjustment to Job Price
*   **Formulas:**
    *   Total Unbillable Time Cost per Job: = (([Average Drive Time per Job] + [Average Setup/Teardown Time per Job]) / 60) * [Hourly Rate for Unbillable Time]
    *   Recommended Adjustment to Job Price: = [Total Unbillable Time Cost per Job]

### 4.8. Sheet: Automated Pricing Data
*   **Purpose:** Estimates labor and chemical costs based on service area size and productivity rates, providing a suggested base price.
*   **Key Inputs:**
    *   Service Area Size (sq ft)
    *   Number of Cleaners
    *   Productivity Rate (sq ft/hr/cleaner)
    *   Chemical Product Usage Rate (ml/sq ft)
    *   Chemical Unit Cost ($/ml)
    *   Desired Chemical Markup (%)
    *   Desired Profit Margin (%) (linked from Pricing Strategy)
*   **Key Outputs:**
    *   Estimated Labor Hours
    *   Estimated Chemical Cost
    *   Suggested Base Price
*   **Formulas:**
    *   Estimated Labor Hours: = [Service Area Size] / ([Number of Cleaners] * [Productivity Rate])
    *   Estimated Chemical Cost: = ([Service Area Size] * [Chemical Product Usage Rate] * [Chemical Unit Cost]) * (1 + [Desired Chemical Markup])
    *   Suggested Base Price: = ([Estimated Labor Hours] * 'Job Costing'!B5 + [Estimated Chemical Cost]) / (1 - 'Pricing Strategy'!B2) (Example cell references for Hourly Labor Rate and Desired Profit Margin)

## 5. Dependencies
*   None (Standard Microsoft Excel functionality only).

## 6. API Endpoint Signatures
N/A - This is an Excel workbook, not a web application with API endpoints. The "API" is the defined structure and formulas within the Excel sheets.
