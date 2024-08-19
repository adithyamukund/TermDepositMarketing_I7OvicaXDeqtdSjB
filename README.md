# Term Deposit Marketing

This project is designed to help a European bank increase subscriptions to their term deposit product. A call center calls its customers to get them to subscribe. The call center collects data about the customer and the call to the customer. 

## Project Overview

The goal of this project is to increase the number of customer subscriptions while improve the efficiency of the bank's call campaigns. Specifically:

1. Predict whether a customer will subscribe.
2. Determine which customers to prioritize for marketing campaigns.
3. Profile customers and subscribers.

## Data Description
- 40,000 rows (call center information for 40,000 customers)
- 13 columns with customer and call info (bank balance, call duration, age etc.), and 1 yes/no column for whether the customer is a subscriber
- 7% of the customers are subscribers.
- 117 days worth of calls to customers (call duration)

## Business Impact

1. Targeted Marketing: Focus marketing efforts on those predicted to subscribe.
2. Efficient Marketing: Reduce customer outreach effort by eliminating customers unlikely to subscribe from call lists.
3. Subscriber segmentation: Group subscribers into various demographic groups for further targeted marketing.

## Methodology

A three-model approach addresses the goals and business impact: 

### Model 1
- Identify customers who should be targeted for initial call campaigns using customer specific features (i.e. exclude call features like duration, times contacted etc.)
- Justification: Call-related features unavailable until calls are made. Goal is to minimize customer call effort.
- Evaluate different ML classifiers
- Success measure: high recall (7% of the data are subscribers)

### Model 2
- Identify customers within a call campaign who are likely to subscribe, using customer and call related features. Input is the output of Model 1.
- Justification: More information (features) to determine whether a customer will subscribe. Determines which customer to KEEP on calling.
- Evaluate different ML classifiers
- Success measure: high precision (to prevent calling customers unlikely to subscribe)

### Model 3
- Segment the subscribers to allow the bank to tailor marketing efforts according to different customer segments.
- Justification: Better understanding of who the subscribers are.
- Evaluate different unsupervised techniques.
- Success measure: minimial variance in each cluster.

## Dashboards
The project includes two interactive dashboards that provide insights into:
- [Customer profiles](https://public.tableau.com/app/profile/adithya.mukund/viz/TermDepositMarketingCustomers/Basics?publish=yes) (both subscribing and non-subscribing).
- [Segmentation of subscriber base](https://public.tableau.com/app/profile/adithya.mukund/viz/TermDepositMarketingSubscribers/Profiles?publish=yes) for more targeted marketing. 

## Installation

To run the project notebook (Project2.ipynb), install the required packages:

_pip install -r requirements.txt_

This ensures that the models run consistently across all computing environments.

## Conclusion

### Model 1
1. Drop all features except balance and age.
2. Standardize and reclassify each point as a no or maybe, using a maximum 0.01 distance from any point to a yes point to reclassify as maybe.
3. Train a random forest with min_samples_leaf=10 on the reclassified data.

Recall: 77%
Business impact: initial call list is 30% reduction from the original set of customers

### Model 2

1. Run Model 1 on entirety of original dataset.
2. Drop all features except balance, age, duration, and call date.
3. Standardize and reclassify each point as a no or maybe, using a distance k between 0.15 and 0.20 to a yes point. Accuracy and recall will always be good regardless of value of k, but to get at least 50% precision, k needs to be at least 0.15.
4. Train a random forest with min_samples_leaf=10 on the reclassified data.

![Screenshot 2024-08-19 at 11 55 00 AM](https://github.com/user-attachments/assets/0bccae67-c9f2-4dec-ac86-ea362454daa4)

Percent of customers elimintated for future calls decreases as precision score increases. Bank needs to decide which one is more important, and choose k accordingly.

### Model 3

There are 4 segments of subscribers customers, which are detailed in the [subscriber dashboard](https://public.tableau.com/app/profile/adithya.mukund/viz/TermDepositMarketingSubscribers/Profiles?publish=yes):

1. Young, single folks with a home loan
2. Middle aged married folks with a home loan. Significantly more effort campaigning to them than other groups.
3. Relatively old married folks without a home loan. Many are retirees.
4. Rich middle aged folks without a home loan and more education than other groups.

Recommendation: focus marketing efforts on the first three groups. The fourth group is only 5% of the data, and has high variance within the cluster.

### Final Thoughts

This project not only predicts the likelihood of customer subscription but also streamlines the call campaign process, reducing the effort required by the call center and improving the bank's marketing effectiveness.
