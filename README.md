# In-Vehicle Coupon Recommendation


### Abstract: This data studies whether a person will accept the coupon recommended to him in different driving scenarios


## Source

https://archive.ics.uci.edu/ml/datasets/in-vehicle+coupon+recommendation

Tong Wang, tong-wang '@' uiowa.edu, University of Iowa
Cynthia Rudin, cynthia '@' cs.duke.edu, Duke University


## Data Set Information

This data was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he/she is the driver.


## Attribute Information

destination: No Urgent Place, Home, Work

passanger: Alone, Friend(s), Kid(s), Partner (who are the passengers in the car)

weather: Sunny, Rainy, Snowy

temperature:55, 80, 30

time: 2PM, 10AM, 6PM, 7AM, 10PM

coupon: Restaurant(<$20), Coffee House, Carry out & Take away, Bar, Restaurant($20-$50)

expiration: 1d, 2h (the coupon expires in 1 day or in 2 hours)

gender: Female, Male

age: 21, 46, 26, 31, 41, 50plus, 36, below21

maritalStatus: Unmarried partner, Single, Married partner, Divorced, Widowed

has_Children:1, 0

education: Some college - no degree, Bachelors degree, Associates degree, High School Graduate, Graduate degree (Masters or Doctorate), Some High School

occupation: Unemployed, Architecture & Engineering, Student,
Education&Training&Library, Healthcare Support,
Healthcare Practitioners & Technical, Sales & Related, Management,
Arts Design Entertainment Sports & Media, Computer & Mathematical,
Life Physical Social Science, Personal Care & Service,
Community & Social Services, Office & Administrative Support,
Construction & Extraction, Legal, Retired,
Installation Maintenance & Repair, Transportation & Material Moving,
Business & Financial, Protective Service,
Food Preparation & Serving Related, Production Occupations,
Building & Grounds Cleaning & Maintenance, Farming Fishing & Forestry

income: $37500 - $49999, $62500 - $74999, $12500 - $24999, $75000 - $87499,
$50000 - $62499, $25000 - $37499, $100000 or More, $87500 - $99999, Less than $12500

Bar: never, less1, 1-3, gt8, nan4-8 (feature meaning: how many times do you go to a bar every month?)

CoffeeHouse: never, less1, 4-8, 1-3, gt8, nan (feature meaning: how many times do you go to a coffeehouse every month?)

CarryAway:n4-8, 1-3, gt8, less1, never (feature meaning: how many times do you get take-away food every month?)

RestaurantLessThan20: 4-8, 1-3, less1, gt8, never (feature meaning: how many times do you go to a restaurant with an average expense per person of less than $20 every month?)

Restaurant20To50: 1-3, less1, never, gt8, 4-8, nan (feature meaning: how many times do you go to a restaurant with average expense per person of $20 - $50 every month?)

toCoupon_GEQ15min:0,1 (feature meaning: driving distance to the restaurant/bar for using the coupon is greater than 15 minutes)

toCoupon_GEQ25min:0, 1 (feature meaning: driving distance to the restaurant/bar for using the coupon is greater than 25 minutes)

direction_same:0, 1 (feature meaning: whether the restaurant/bar is in the same direction as your current destination)

direction_opp:1, 0 (feature meaning: whether the restaurant/bar is in the same direction as your current destination)

Y:1, 0 (whether the coupon is accepted)


## Data Preparation

Code Used: Python

Packages: Pandas, Numpy, Matplotlib, Seaborn

## Data Cleansing

There are 74 duplicated rows, 99% missing values in 'Car' column, and 1% missing values in 'CoffeeHouse', 'CarryAway', 'RestaurantLessThan20', 'Restaurant20To50' columns. So we will remove duplicate rows, 'Car' column, and fill the missing values in 'CoffeeHouse', 'CarryAway', 'RestaurantLessThan20', 'Restaurant20To50' with Mode value since the column value is categorical.

From the Multicolinearity study, we found that 'direction_opp' and 'direction_same' has correlation value of -1. So we need to choose only one of them. We will proceed with column 'direction_same' and remove 'direction_opp'.


## Some Modeling

Step 3-9 (7-8-9 pending)


## Independent investigation

Observations:

destination to Y relation: The possibility of accepting the coupon is higher when the drivers have no urgent place to go.

passenger to Y relation: The possibility of accepting the coupon is higher when the driver is alone.

weather to Y relation: The possibility of accepting the coupon is higher when it is sunny.

temperature to Y relation: The possibility of accepting the coupon is higher when when it is 80 degrees.

time to Y relation: The probability of accepting the coupon is higher, if the time is 6pm or 7pm, and not during the day.

coupon to Y relation: 1) The possibility of accepting coupons for resturants that cost less than 20 dollars, carry out and take away is high. 2) The acceptance and rejection of coffee house coupons is equal. 3) coupons for bars and resturants that cost between 20-50 dollars have a higher rejection rate.

expiration to Y relation: Coupon that expire in one day have higher acceptance rate than the ones expiring in two hours.

gender to Y relation: Both genders have the same rates.

age to Y relation: drivers between 21 to 36 years old accept more coupons.

maritalStatus to Y relation: Single drivers accept the coupons more.

has_children to Y relation: Driver's who do not have children are more likely to accept coupons.

education to Y relation: Some college, Bachelor or high school graduate are more likely to accept the coupon.

occupation to Y relation: drivers who are unemployed, students, work in sales, or computers have the highest tendency to accept the copouns.

income to Y relation: middle class drivers have a higher tendency to accept the copouns.

Bar to Y relation: The lower the frequancy of visits the higher possiblity of accepting the copoun.

CoffeeHouse to Y relation: moderate frequancy of visits has a higher possiblity of accepting the coupon.

CarryAway to Y relation: moderate frequancy of visits has a higher possiblity of accepting the coupon.

RestaurantLessThan20 to Y relation: moderate frequancy of visits has a higher possiblity of accepting the coupon. Restaurant20To50 to Y relation: if the driver went less than once they have a higher tendancy of accepting the copoun. toCoupon_GEQ15min to Y relation: not much difference toCoupon_GEQ25min to Y relation: if the distance is less than 25mins to the ccpou location it will be more likley to be accepted. direction_same to Y relation: if the direction is not the same, the coupons get purchased more.




