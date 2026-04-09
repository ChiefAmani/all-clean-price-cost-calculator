# Technical Specification: Profit Per Job Calculator (Excel)

This document outlines the technical specifications for the Excel-based "Profit Per Job Calculator." It details the workbook structure, sheet-specific inputs, calculations, and expected outputs, directly referencing the financial models defined in `FINANCIAL_MODELS.md`.

## 1. Workbook Structure

The Excel workbook `profit_per_job_calculator.xlsx` will consist of the following sheets:

*   **Dashboard:** Executive summary and key performance indicators.
*   **Job Costing:** Detailed calculation of costs and profit for individual jobs.
*   **Overhead & Break-Even:** Analysis of fixed/variable costs and break-even points.
*   **Pricing Strategy:** Tools for optimal pricing, including "Are You Undercharging?" and tiered pricing.
*   **Equipment ROI:** Calculates return on investment for equipment purchases.
*   **Employee Compensation:** Models various employee payment structures.
*   **Drive Time & Setup Allocation:** Accounts for unbillable time.
*   **Automated Pricing Data:** Estimates costs based on service area and productivity.

## 2. Sheet-Specific Specifications

### 2.1. Dashboard

*   **Purpose:** Provide a high-level overview of the business's financial health and key metrics.
*   **Inputs:** None (all data derived from other sheets).
*   **Outputs:**
    *   Average Profit per Job (linked from 'Job Costing')
    *   Total Monthly Profit (Est) (linked from 'Job Costing' and 'Overhead & Break-Even')
    *   Break-Even Number of Jobs (linked from 'Overhead & Break-Even')
*   **Formulas:** As defined in `FINANCIAL_MODELS.md` under "Dashboard Summary".

### 2.2. Job Costing

*   **Purpose:** Calculate the direct costs and gross profit for a single job. This is the core "Profit Per Job" calculation.
*   **Inputs:**
    *   Total Job Price (Revenue)
    *   Estimated Labor Hours
    *   Hourly Labor Rate
    *   Other Direct Costs (e.g., consumables not chemicals)
    *   Estimated Callback Hours
    *   Callback Hourly Rate
    *   Callback Material Cost
    *   Total Chemical Cost (can be manually entered or linked from 'Automated Pricing Data')
*   **Outputs:**
    *   Total Labor Cost
    *   Total Callback Cost
    *   Total Direct Job Cost
    *   Gross Profit per Job
    *   Gross Profit Margin (%)
*   **Formulas:** As defined in `FINANCIAL_MODELS.md` under "Job Costing".

### 2.3. Overhead & Break-Even

*   **Purpose:** Determine the fixed and variable overheads and calculate the break-even point.
*   **Inputs:**
    *   Monthly Fixed Costs (e.g., rent, insurance, software subscriptions)
    *   Monthly Variable Overhead (e.g., fuel, office supplies)
    *   Average Direct Cost per Job (linked from 'Job Costing' or user input for estimation)
    *   Average Revenue per Job (linked from 'Job Costing' or user input for estimation)
*   **Outputs:**
    *   Total Monthly Overhead
    *   Contribution Margin per Job
    *   Break-Even Number of Jobs
    *   Break-Even Revenue
*   **Formulas:** As defined in `FINANCIAL_MODELS.md` under "Overhead & Break-Even".

### 2.4. Pricing Strategy

*   **Purpose:** Assist in setting profitable prices and identify if current pricing is adequate.
*   **Inputs:**
    *   Desired Profit Margin (%)
    *   Total Estimated Job Cost (linked from 'Job Costing' or user input)
    *   Base Price for Good/Better/Best (user input)
    *   Markup % for Better Tier (user input)
    *   Markup % for Best Tier (user input)
*   **Outputs:**
    *   Suggested Minimum Profitable Price ("Are You Undercharging?" indicator)
    *   Good Tier Price
    *   Better Tier Price
    *   Best Tier Price
*   **Formulas:** As defined in `FINANCIAL_MODELS.md` under "Pricing Strategy".

### 2.5. Equipment ROI

*   **Purpose:** Calculate the return on investment for new equipment purchases.
*   **Inputs:**
    *   Purchase Price
    *   Estimated Lifespan (Years)
    *   Estimated Maintenance Cost (Annual)
    *   Estimated Revenue Increase/Cost Savings per Job
    *   Average Jobs per Month
*   **Outputs:**
    *   Monthly Depreciation
    *   Total Annual Cost of Equipment
    *   Jobs to Break Even (ROI)
    *   Time to Break Even (Months)
*   **Formulas:** As defined in `FINANCIAL_MODELS.md` under "Equipment ROI".

### 2.6. Employee Compensation

*   **Purpose:** Model different employee compensation structures and their impact on job profitability.
*   **Inputs:**
    *   Base Hourly Rate
    *   Commission Rate (%)
    *   Performance Bonus Criteria ($)
    *   Job-specific Revenue (linked from 'Job Costing' or user input)
*   **Outputs:**
    *   Total Labor Cost per Job (including commission/bonus)
    *   Net Profit after Employee Compensation
*   **Formulas:** As defined in `FINANCIAL_MODELS.md` under "Employee Compensation".

### 2.7. Drive Time & Setup Allocation

*   **Purpose:** Account for unbillable time (drive, setup, teardown) and its cost impact.
*   **Inputs:**
    *   Average Drive Time per Job (minutes)
    *   Average Setup/Teardown Time per Job (minutes)
    *   Hourly Rate for Unbillable Time (e.g., average employee hourly rate)
*   **Outputs:**
    *   Total Unbillable Time Cost per Job
    *   Recommended Adjustment to Job Price
*   **Formulas:** As defined in `FINANCIAL_MODELS.md` under "Drive Time & Setup Allocation".

### 2.8. Automated Pricing Data

*   **Purpose:** Provide automated estimates for labor and chemical costs based on job parameters.
*   **Inputs:**
    *   Service Area Size (e.g., sq ft for house washing, linear ft for gutters)
    *   Number of Cleaners
    *   Productivity Rate (e.g., sq ft/hr/cleaner)
    *   Chemical Product Usage Rate (e.g., ml/sq ft)
    *   Chemical Unit Cost ($/ml)
    *   Desired Chemical Markup (%)
*   **Outputs:**
    *   Estimated Labor Hours
    *   Estimated Chemical Cost
    *   Suggested Base Price (linked to 'Pricing Strategy' desired margin)
*   **Formulas:** As defined in `FINANCIAL_MODELS.md` under "Automated Pricing Data".

## 3. Implementation Details

*   **Cell Referencing:** Formulas will use direct cell references within and between sheets as specified in `FINANCIAL_MODELS.md`.
*   **Formatting:**
    *   Input cells will be clearly identifiable (e.g., specific fill color).
    *   Output cells will be formatted appropriately (currency, percentage, number).
    *   Headers will be bold and clearly label sections.
    *   Conditional formatting may be used (e.g., for "Are You Undercharging?" to highlight if profit margin is below desired).
*   **Data Validation:** Where appropriate, data validation will be used for input cells (e.g., percentage inputs between 0-100%).
*   **Protection:** Sheets containing formulas will be protected to prevent accidental modification, allowing only input cells to be edited.
