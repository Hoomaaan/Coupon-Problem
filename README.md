# Coupon-Problem
Imagine driving through town and a coupon is delivered to your cell phone for a restaraunt near where you are driving. Would you accept that coupon and take a short detour to the restaraunt? Would you accept the coupon but use it on a sunbsequent trip? Would you ignore the coupon entirely? What if the coupon was for a bar instead of a restaraunt? What about a coffee house? Would you accept a bar coupon with a minor passenger in the car? What about if it was just you and your partner in the car? Would weather impact the rate of acceptance? What about the time of day?

Obviously, proximity to the business is a factor on whether the coupon is delivered to the driver or not, but what are the factors that determine whether a driver accepts the coupon once it is delivered to them? How would you determine whether a driver is likely to accept a coupon?

### Overview 

The goal of this project is to use what you know about visualizations and probability distributions to distinguish between customers who accepted a driving coupon versus those that did not.

### Data

This data comes to us from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he is the driver. Answers that the user will drive there ‘right away’ or ‘later before the coupon expires’ are labeled as ‘Y = 1’ and answers ‘no, I do not want the coupon’ are labeled as ‘Y = 0’. There are five different types of coupons -- less expensive restaurants (under $20), coffee houses, carry out & take away, bar, and more expensive restaurants ($20 - $50).

### Data Description
Keep in mind that these values mentioned below are average values.

The attributes of this data set include:

_User attributes_

Gender: male, female

Age: below 21, 21 to 25, 26 to 30, etc.

Marital Status: single, married partner, unmarried partner, or widowed

Number of children: 0, 1, or more than 1

Education: high school, bachelors degree, associates degree, or graduate degree

Occupation: architecture & engineering, business & financial, etc.

Annual income: less than $12500, $12500 - $24999, $25000 - $37499, etc.

Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8

Number of times that he/she buys takeaway food: 0, less than 1, 1 to 3, 4 to 8 or greater than 8

Number of times that he/she goes to a coffee house: 0, less than 1, 1 to 3, 4 to 8 or greater than 8

Number of times that he/she eats at a restaurant with average expense less than $20 per person: 0, less than 1, 1 to 3, 4 to 8 or greater than 8

Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8

Contextual attributes

Driving destination: home, work, or no urgent destination

Location of user, coupon and destination: we provide a map to show the geographical location of the user, destination, and the venue, and we mark the distance between each two places with time of driving. The user can see whether the venue is in the same direction as the destination.

Weather: sunny, rainy, or snowy

Temperature: 30F, 55F, or 80F

Time: 10AM, 2PM, or 6PM

Passenger: alone, partner, kid(s), or friend(s)

_Coupon attributes_

time before it expires: 2 hours or one day

# Analysis

To gain an overall understanding of the dataset, I conducted a set of descriptive statistics. Handling missing values involved dropping relevant rows, and detailed data cleaning and preprocessing steps can be found in the accompanying notebook.

Upon further investigation, it became evident that coffee houses had the highest number of coupons in the dataset. This analysis focuses on identifying factors influencing drivers' acceptance or rejection of a coffee house coupon.
![allCoupons](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/82126045-cc38-4d3d-ad70-855839c13744)

In the above plot, Y = 1 means coupon is accepted, otherwise, Y = 0;
### Coupon Acceptance Ratio
I began by determining the acceptance ratio of coffee house coupons compared to all coupons and specific times. See the chart below:

![cofferation](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/1ac4400e-108e-45bb-ba2a-18a8b5b4bc8d)

### Weather Impact

Exploring the impact of weather on coupon acceptance, I plotted different weather types against the number of accepted and rejected coupons.

![weatherImpact](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/c26cc1dd-f57c-40d8-a570-809ea980386f)
![newplot](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/5d150ca4-314c-4eb2-84c8-5ae0db87130e)

The plot indicates that sunny and rainy days tend to have a slightly higher number of accepted coupons. Conversely, snowy days show more rejections, suggesting weather influences acceptance. Additionally, I highlighted the distribution of coupons based on weather types, with approximately 86.9% distributed on sunny days.

### Passenger Type Influence

Analyzing the effect of passenger type on coupon acceptance/rejection, I created a bar plot based on accepted and rejected coffee house coupons for different passenger types.

![newplot (2)](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/3f595e94-91ec-4e40-a6ec-99db5de598f6)

The plot shows that solo drivers receive the highest number of coupons, regardless of acceptance or rejection. Notably, solo drivers tend to reject coupons more often, while drivers with friends or partners accept them more frequently. This insight can guide coupon distribution strategies to maximize revenue.

### Time-of-Day and Passenger Type
Examining the interaction between time-of-day and passenger type, I found that drivers with friends are more likely to accept coffee shop coupons throughout the day.

![newplot (3)](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/d3fe8bec-06c7-4cd6-b812-04d774ab85a8)

However, solo drivers tend to reject coupons, except at 10 AM, making mornings the optimal time to provide coupons to alone drivers.

![newplot (4)](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/08e540bd-ee3a-4a5a-903c-03fa6c1b6040)

As these two graphs show, 10 AM is the best time that has the highest number of acceptances compared to other times no matter if the driver is alone or with a friend. This will help the coffee houses know what time of the day is the best time to bring in more customers. This makes me curious to see how other passengers affect the outcome.

![newplot (5)](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/7bb41fd0-e165-442e-9a6b-dfbde5c6079f)

For drivers with kids, the accepted coupon count decreases as the evening approaches.

Lastly, the optimal times for coupon acceptance for drivers with partners are around 10 AM or 6 PM.

![newplot (6)](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/31d81b39-cd94-4fd0-8b48-97693538685a)

Another hypothesis that I had during the analysis was the higher income reduces the acceptance of the coupon. Therefore, in the next section, I considered the impact of the annual income.

### Income Impact

Considering the impact of annual income on coupon acceptance, the following plots illustrate the number of coupons based on income groups. Surprisingly, the lowest and highest income groups show the highest received coupons, while the middle-income group (75K to 87.5K) has the lowest acceptance.

![test](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/bb3ae144-7e94-4b45-ab6f-d9dffe429a47)

To be more concise, I calculated the acceptance rate of the coupon based on the income groups.

![image](https://github.com/Hoomaaan/Coupon-Problem/assets/33916130/3f241208-2125-4b15-ae3c-19370cedd440)

The acceptance rate also proves that middle-class people with an average income of 75k to 87.5k have the lowest acceptance rate for coffee house coupons.

All in all, various factors such as weather, passenger type, and income influence the likelihood of accepting or rejecting a coupon. Future analyses could explore additional factors like road congestion, coffee house pricing, and coffee quality to deepen our understanding of the decision-making process. It would also be interesting to see whether the same factors are playing a role in other types of coupons.

_P.S: In the Python notebook, I tried to use all three plotting libraries such as matplotlib, seaborn, and plotly to better practice all of them_

_P.S.2:It looks like the plots I have generated using Plotly packages are note visible in the github. Therefore, to see the plots, please download the Python notebook._
