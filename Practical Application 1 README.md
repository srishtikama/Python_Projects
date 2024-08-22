# Assignment
Determine whether a driver is likely to accept a coupon using a multide of different factors.

# Data
This data comes from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he is the driver. Within the data, there are 7 driver description columns, 5 columns describing the number of times the driver goes to various locations, 6 columns describing the driver's location and the time the survey was taken, and columns describing the coupon attributes for a total of 26 columns and 12,684 rows.

## Data Changes Made
- Removed car column because ~99% of the data was missing from this column
- Dropped missing rows from columns: Bar, CoffeeHouse, Restaurant20To50, RestaurantLessThan20, CarryAway
- Total rows dropped were 605

# Guided Investigation
Within the cleaned data set, 57% of the drivers chose to accept the coupon. To investigate this further, I analyzed which factors affect acceptance of Bar coupons. and whether destination had an effect on coupon acceptance. 

## Bar Coupon Acceptance Findings
- About 41% of bar coupons were accepted
- Acceptance Rate of those who went to a bar 3 or fewer times: 33.51% | Acceptance Rate of those who went to a bar more than 3 times: 7.68%
- Acceptance Rate of those who went to a bar more than once a month and over 25: 14.53% | Acceptance Rate of others: 26.66%
- Acceptance Rate of those who went to a bar more than once a month and passengers that were not a kid and had occupations other than farming, fishing, or forestry: 19.65% | Acceptance Rate of others: 21.54%
- Acceptance Rate of those who go to bars more than once a month, had passengers that were not a kid, and were not widowed = 19.65%
- Acceptance Rate of those who go to bars more than once a month and are under the age of 30 = 12.13%
- Acceptance Rate of those who go to cheap restaurants more than 4 times a month and income is less than 50K = 7.95%

### Final Findings
Based on these observations, people who go the bar more than once a month and accept the coupon generally are more likely to not have had a kid as a passenger and were widowed. Also people who go to the bar once a month and accept the coupon were more likely be younger, under the age of 30, and have income more than 50K. Looking at the acceptance rates in question 5, people who went to the bar at most 3 times in a month were more likely to accept the bar coupon than not but the acceptance rate decreases when looking at people who go to the bar more than once a month along with other factors. There is a bit of overlap in these populations but one explanation could be that people who usually don't go to the bar, would accept a coupon to go because otherwise they will not.

# Independent Investigation
Within the cleaned data set, 57% of the drivers chose to accept the coupon. To investigate this further, I analyzed whether destination had an effect on coupon acceptance. Based on the "Driver Count by Destination and Coupon Acceptance" plot, it seems like the acceptance rate is about equal for each destination with "No Urgent Place" having a 60-40 split between coupon accepted and not accepted. Now I will see if the following features change the acceptance rate for each destination:
- Gender
- marital Status
- Carry Away frequency
- Any combination of the above

## Driver Destination on Coupon Acceptance Findings
- Regardless of gender, drivers are more likely to accept the coupon if they are going to "No Urgent Place".
- For all destinations, males are slightly more likely to accept the coupon than females with the biggest difference between gender coming when drivers are going home.
- The highest coupon acceptance rate occurs when a driver is going "No Urgent Place" and has a married partner at ~12.4% acceptance.
- The next highest has a very similar acceptance rate, ~12.3%, and occurs when a driver is again going "No Urgent Place" but is single.
- The marital status of the driver does seem to affect coupon acceptance as drivers that are divorced or widowed have extremely low acceptance rates, 1% or less, compared to single drivers or drivers with partners.
- Regardless of driver destination, there are equal proportions of drivers Carrying Away food 1-3 times a month and 4-8 times a month.
- There are equal proportions of drivers Carrying Away food less than once a month and never.
- On average, male drivers have a about a 3% higher acceptance rate than females when going "No Urgent Place".
- In general for all CarryAway frequencies, driver are more likely to accept the coupon than not accept when they never CarryAway.
- The highest coupon acceptance rate, at ~9.9%, are drivers who have a married partner and CarryAway between 1-3 times a month.
- Drivers who are divorced or widowed have a less than 1% coupon acceptance rate.

# Next Steps
Using the findings listed above, further analysis can be done on other columns to see if there are further correlations that can be seen in the data. After any additional findings are discovered, we can move on to predicting whether a driver will accept the coupon. The factors that could affect the prediction are:
- Marital Status
- Destination
- Type of Coupon

# Link to Code
[prompt.ipynb](https://github.com/srishtikama/Python_Projects/blob/main/prompt.ipynb)

