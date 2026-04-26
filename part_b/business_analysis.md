#(a) Machine Learning Problem Formulation#
The problem can be formulated as a supervised regression task.
Target Variable: items_sold (sales volume per store per month).
Candidate Input Features:
Store attributes: size, location type, footfall, competition density, demographics.
Promotion type: Flat Discount, BOGO, Free Gift, Category Offer, Loyalty Points.
Calendar features: month, season, festival flag, weekend flag.
Historical performance: lagged sales, moving averages.

Justification: Regression is appropriate because the target is a continuous variable (number of items sold). Classification (e.g., “high vs low sales”) would oversimplify the problem and lose business nuance.


