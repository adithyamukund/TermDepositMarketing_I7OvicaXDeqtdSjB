# Term Deposit Marketing

This project is designed to help a European bank increase subscriptions to their term deposit product by optimizing call center efforts. The dataset includes call center data for 40,000 customers, of which only about 7% are current subscribers. The data includes both customer information (e.g., age, bank balance) and call-related data (e.g., number of contacts, length of the last call).

## Project Overview

The goal of this project is to improve the efficiency of the bank's call campaigns by:

1. Predicting which customers the bank should initiate a call campaign with.
2. Predicting which customers in a call campaign are likely to subscribe, so the bank knows who to keep calling.
3. Segmenting subscribers to determine how to target marketing efforts more effectively.

A three model approach achieves this goal.

## Models

1. Identifies customers who should be targeted for initial call campaigns.
2. Identifies customers within a call campaign who are likely to subscribe, enabling the bank to focus efforts on these individuals.
3. Segments the subscribers to allow the bank to tailor marketing efforts according to different customer segments.

## Dashboards
The project includes two interactive dashboards that provide insights into:
- [Customer profiles](https://public.tableau.com/app/profile/adithya.mukund/viz/TermDepositMarketingCustomers/Basics?publish=yes) (both subscribing and non-subscribing).
- [Segmentation of subscriber base](https://public.tableau.com/app/profile/adithya.mukund/viz/TermDepositMarketingSubscribers/Profiles?publish=yes) for more targeted marketing. 

## Installation

To run the project notebook (Project2.ipynb), install the required packages:

_pip install -r requirements.txt_

This ensures that the models run consistently across all computing environments.

## Conclusion

This project not only predicts the likelihood of customer subscription but also streamlines the call campaign process, reducing the effort required by the call center and improving the bank's marketing effectiveness.
