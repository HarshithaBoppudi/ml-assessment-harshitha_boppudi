**B1. Problem Formulation**
**(a) Machine Learning Problem Formulation**

The problem can be formulated as a supervised regression task.
Target Variable: items_sold (sales volume per store per month).
Candidate Input Features:
Store attributes: size, location type, footfall, competition density, demographics.
Promotion type: Flat Discount, BOGO, Free Gift, Category Offer, Loyalty Points.
Calendar features: month, season, festival flag, weekend flag.
Historical performance: lagged sales, moving averages.

Justification: Regression is appropriate because the target is a continuous variable (number of items sold). Classification (e.g., “high vs low sales”) would oversimplify the problem and lose business nuance.

**(b) Why Items Sold is a Better Target**
Revenue can be distorted by pricing strategies (e.g., high-value items inflating revenue even if few units are sold). In contrast, items sold reflects customer response to promotions more directly, independent of price fluctuations.

Broader Principle: Target variables must align with the true business objective. In ML projects, choosing a target that faithfully represents the phenomenon of interest (here, promotion effectiveness) is more important than picking a convenient or traditional metric.

**(c) Modelling Strategy Beyond a Global Model**
A single global model ignores heterogeneity across stores. Urban stores may respond strongly to loyalty points, while rural stores may prefer flat discounts.

Alternative Strategy:

Build a hierarchical (multi-level) model that shares global patterns but allows store-specific adjustments.

Or cluster stores by similarity (location type, demographics, competition) and train segmented models per cluster.

This balances scalability with local responsiveness.


**B2. Data and EDA Strategy — 10 marks
(a) Data Integration**
The four tables (transactions, store attributes, promotion details, calendar) would be joined using store_id and transaction_date as keys.

Grain of final dataset: One row = one store’s monthly aggregated performance under a given promotion.

Aggregations:

Sum of items sold per store per month.

Average competition density.

Promotion type applied that month.

Flags for weekends/festivals aggregated to monthly counts.

**(b) Exploratory Data Analysis (EDA)**
Key analyses before modelling:

Promotion vs Items Sold (bar chart)

Compare average sales volume across promotions.

Guides feature importance expectations.

Location Type vs Promotion Effectiveness (grouped bar chart)

Check if rural vs urban stores respond differently.

Informs segmentation strategy.

Seasonality Trends (line chart over months)

Identify peaks (festivals, end-of-season sales).

Suggests adding temporal features.

Competition Density vs Sales (scatter plot)

Test correlation between local competition and promotion success.

Helps decide whether to scale promotions differently in high-density markets.

**(c) Handling Promotion Imbalance**
With 80% of transactions having no promotion, the model risks learning a bias toward “no promotion” as the default.

Mitigation Steps:

Use resampling techniques (oversample promotion cases or undersample no-promotion cases).

Apply class weights or balanced loss functions.

Consider modelling uplift (difference in sales with vs without promotion) rather than raw sales.
