Hotel Demand Analysis Report
Introduction:
This purpose of this analysis is to explore and gain insights from a dataset related to hotel bookings. The dataset includes various attributes such as booking dates, customer information, and hotel preferences. By analyzing this data, we aim to identify key patterns, clean the dataset, detect outliers, and understand correlations among features to support better decision-making in hospitality management.

Dataset Description 
The dataset consists of hotel booking information and contains the following features:
Feature	Description
hotel	Type of hotel: either Resort Hotel or City Hotel.
is_canceled	Whether the booking was canceled (1) or not (0).
lead_time	Number of days between booking date and arrival date.
arrival_date_year	Year of arrival.
arrival_date_month	Month of arrival (e.g., January, February).
arrival_date_week_number	ISO week number of arrival (1–52).
arrival_date_day_of_month	Day of the month of arrival (1–31).
stays_in_weekend_nights	Number of weekend nights (Saturday and Sunday) the guest stayed.
stays_in_week_nights	Number of weekday nights (Monday to Friday) the guest stayed.
adults	Number of adults in the booking.
children	Number of children in the booking.
babies	Number of babies in the booking.
meal	Type of meal booked (e.g., BB = Bed & Breakfast, HB = Half Board, FB = Full Board, SC = Self Catering).
country	Country of origin of the guest (ISO 3166-1 alpha-3 country codes).
market_segment	How the booking was made (e.g., Online TA, Corporate, Direct, Offline TA/TO).
distribution_channel	How the booking was distributed to the hotel (e.g., Direct, TA/TO).
is_repeated_guest	Whether the guest is a returning guest (1) or not (0).
previous_cancellations	Number of previous bookings that were canceled by the customer.
previous_bookings_not_canceled	Number of previous bookings not canceled by the customer.
reserved_room_type	Code of the room type reserved by the customer.
assigned_room_type	Code of the room type actually assigned to the customer.
booking_changes	Number of changes/amendments made to the booking.
deposit_type	Type of deposit made (No Deposit, Non Refund, Refundable).
agent	ID of the travel agent that made the booking (or NULL if none).
company	ID of the company that made the booking (or NULL if none).
days_in_waiting_list	Number of days the booking was on the waiting list before being confirmed.
customer_type	Type of customer (e.g., Transient, Contract, Group, Transient-Party).
adr	Average Daily Rate: total revenue / total nights stayed.
required_car_parking_spaces	Number of car parking spaces requested.
total_of_special_requests	Total number of special requests made (e.g., high floor, twin beds).
reservation_status	Final status of the reservation (Canceled, Check-Out, No-Show).
reservation_status_date	Date when the reservation was last updated.
name	Name of the person who made the booking.
email	Email address of the customer.
phone-number	Phone number of the customer.
credit_card	Credit card number used to guarantee the booking.




3. Data Cleaning and Sorting
In this analysis missing values were observed in the columns : children, country, agent and company. These columns are crucial for segmenting customer demographics and booking sources. All rows containing null values were removed using dropna() method.
As a result, the dataset size was significantly reduced from 119,390 entries to only 217 rows, indicating a large proportion of incomplete records.

4.Outliers Detection Using IQR
To identify and handle outliers, the Interquartile Range (IQR) method was applied to key numerical features such as lead_time, adr, and stays_in_week_nights. The first quartile (Q1) and third quartile (Q3) were computed for each feature, and the IQR was calculated as the difference between them.
Data points falling below Q1 − 1.5×IQR or above Q3 + 1.5×IQR were flagged as outliers. Notably, features like lead_time and adr had several high-end outliers, indicating rare but extreme booking behaviors or pricing anomalies. These were retained for analysis to preserve information on possible edge-case scenarios.

Data visualizations
Cancellation rate by Hotel type:
This visualization compares the average cancellation rates across different hotel types, highlighting which hotel category experiences more frequent cancellations.
 

Cancellation  Rate by Customer Type
	This chart illustrates the variation in cancellation rates among different customer types, showing how booking cancellations differ based on the nature of the customer.
 
Cancellation Rate by Season
This graph presents cancellation rates segmented by season, revealing how cancellation behavior changes throughout the year depending on the travel season
 

Booking Trends Over Time
Analysis of booking volume over time reveals distinct patterns in hotel reservation activity. Overall, the number of bookings shows fluctuations, with noticeable peaks and troughs that correspond to seasonal demand and possibly external factors such as holidays or events. Monitoring these trends provides insight into periods of high and low booking activity, enabling better resource planning and marketing efforts.
 
Booking Trends by Hotel Type
When segmented by hotel type, booking trends highlight differences in customer engagement between City Hotels and Resort Hotels. Both hotel types show similar overall patterns, but City Hotels generally maintain steadier booking volumes throughout the year. Resort Hotels exhibit more pronounced peaks, likely reflecting their appeal to vacation travelers and seasonal demand. This differentiation suggests tailored strategies are needed to optimize occupancy for each hotel type, with Resort Hotels requiring more targeted promotions during off-peak periods.
 

ADR Distribution Analysis
The distribution of the Average Daily Rate (ADR) provides valuable insight into pricing strategies and customer spending behavior across the dataset. The histogram with KDE (Kernel Density Estimate) reveals the spread and concentration of ADR values, indicating common price points and the variability in room rates.
Typically, the ADR distribution helps identify the most frequent pricing tiers and detects any skewness or outliers, such as extremely high or low room rates. This understanding complements the earlier findings on booking cancellations and hotel types — for example, higher ADR values may correspond to Resort Hotels or premium customer segments, which may also influence cancellation tendencies and booking volumes.
Analyzing ADR alongside booking trends and cancellation rates enables a holistic view of revenue management. Hotels can leverage this to optimize pricing policies that balance occupancy and profitability, targeting segments less prone to cancellations and adjusting rates seasonally based on demand fluctuations observed in the booking trends.
 

ADR Distribution by Hotel Type
The box plot illustrates the variation in Average Daily Rate (ADR) between different hotel types. It highlights the median ADR, the spread of rates, and the presence of any outliers within each category. Typically, Resort Hotels show a higher median ADR with a wider range, reflecting their premium pricing and seasonal variability. City Hotels tend to have a lower and more consistent ADR, likely due to steady demand from business travelers.
Understanding this distribution helps in tailoring pricing strategies for each hotel type, ensuring competitive rates that align with customer expectations and booking patterns observed in previous analyses.
 

Correlation Heatmap Analysis
The correlation heatmap displays the relationships among key numerical variables such as lead time, average daily rate (ADR), number of adults, children, and cancellation status. Positive or negative correlations indicate how changes in one variable are associated with changes in another.
For example, a positive correlation between lead time and cancellation rate might suggest that bookings made further in advance are more likely to be canceled. The heatmap also helps identify whether ADR is related to group size (adults, children) or cancellations, offering insights into pricing and customer behavior dynamics.
This analysis supports deeper understanding of factors influencing booking cancellations and revenue, enabling more informed decision-making in pricing and customer management strategies.
 
Geographic Analysis: Country-wise Bookings
This visualization presents the distribution of bookings by country, highlighting the geographic origins of hotel guests. By aggregating booking counts per country, it reveals key markets that contribute the most to hotel occupancy. Understanding these patterns helps identify core customer bases and tailor marketing or service offerings to meet the preferences of travelers from high-volume countries. This geographic insight complements the broader analysis of booking behaviors and customer segments, supporting targeted growth strategies.
 

Lead Time vs Cancellation
This scatter plot visualizes the relationship between the booking lead time and cancellation status, with points colored by hotel type. It helps identify whether longer lead times correlate with higher cancellation rates. Patterns here can reveal if customers booking well in advance tend to cancel more often, and if this behavior differs between City and Resort Hotels. Such insights are valuable for managing booking policies and anticipating cancellations based on when reservations are made.
 
Revenue Impact of Cancellations
This analysis quantifies the financial impact of booking cancellations by comparing total potential revenue from canceled and non-canceled reservations. By calculating the revenue per booking as the product of the average daily rate (ADR) and the total nights stayed, it highlights how cancellations reduce overall hotel revenue. The bar plot clearly shows the revenue lost due to cancellations, emphasizing the importance of minimizing cancellations to improve profitability and operational efficiency.
 

Revenue by Market Segment
This analysis breaks down total revenue by different market segments, revealing which customer groups contribute most financially to the hotels. By aggregating the revenue—calculated as the product of ADR and total nights stayed—for each segment, the visualization highlights key revenue drivers. Understanding these differences allows hotels to focus marketing and service efforts on the most profitable segments, optimizing revenue management and strategic planning
 



Demand by ADR Range
This analysis segments bookings by average daily rate (ADR) ranges to assess how demand varies across different price points. The bar plot shows the number of bookings falling within each ADR bracket, highlighting which pricing tiers attract the most customers. This information is crucial for pricing strategy, as it identifies the sweet spots where demand is highest and helps balance revenue goals with occupancy rates.
 

Cancellation Rate by Customer Type
This visualization shows the average cancellation rates across different customer types. By comparing these rates, it highlights which customer segments are more likely to cancel their bookings. Understanding these differences helps hotels develop targeted strategies to reduce cancellations, improve customer retention, and optimize booking reliability.
 


Cancellation Rate vs Lead Time
This analysis examines how the likelihood of cancellation varies with the booking lead time, grouped into ranges of days before arrival. The line plot reveals trends indicating whether longer or shorter lead times are associated with higher cancellation rates. Such insights help hotels manage booking policies, such as deposits or flexible cancellation options, based on how far in advance customers book.
 

Special Requests vs Cancellation
This box plot compares the distribution of the number of special requests made by guests in canceled versus non-canceled bookings. It helps identify whether guests who make more special requests are more or less likely to cancel their reservations. Such insights can guide customer service strategies to better engage guests and potentially reduce cancellations.
 

Booking Demand by Month
This visualization shows the distribution of hotel bookings across each month, highlighting peak and off-peak seasons. By identifying months with the highest booking demand, hotels can optimize staffing, marketing efforts, and pricing strategies to maximize occupancy and revenue during busy periods while managing resources efficiently during slower months
 

Monthly Booking Patterns by Hotel Type
This analysis compares booking volumes for City and Resort hotels across months, revealing how seasonal trends differ between hotel types. The bar chart highlights periods of peak demand specific to each hotel category, helping identify when and where marketing and operational efforts should be focused. Understanding these patterns enables hotels to better manage capacity, pricing, and promotional strategies aligned with customer preferences and seasonal variations
 
Average Daily Rate (ADR) Distribution
This histogram displays the distribution of the Average Daily Rate (ADR) across all bookings, showing how frequently different price points occur. Including a kernel density estimate (KDE) provides a smooth curve to better understand the overall pricing trends and detect common pricing clusters or outliers. This insight aids in evaluating pricing strategies and identifying opportunities to optimize rates based on customer willingness to pay.
 

Top 10 Countries by Bookings
This analysis highlights the countries contributing the highest number of bookings to the hotels. By focusing on the top ten countries, the bar plot reveals key source markets driving hotel demand. Understanding this geographic distribution supports targeted marketing, tailored services, and strategic partnerships to attract and retain customers from these important regions.
 
Bookings by Market Segment
This analysis shows the distribution of bookings across various market segments, highlighting which segments contribute most to booking volume. The bar plot helps identify key customer sources—such as online travel agents, direct bookings, or corporate clients—informing marketing focus and resource allocation to maximize bookings from the most productive segments.

 

Average Revenue by Market Segment
This visualization illustrates the average revenue generated per booking across different market segments, calculated as the product of the average daily rate and total nights stayed. It reveals which segments contribute higher-value bookings, providing insights for revenue management and prioritizing marketing efforts toward the most profitable customer sources.
 
Bookings by Distribution Channel
This analysis shows the volume of bookings coming through different distribution channels, such as direct bookings, travel agents, or online platforms. Understanding which channels drive the most bookings helps hotels optimize their distribution strategies, allocate marketing budgets effectively, and strengthen partnerships with key channels to maximize booking inflow.
 

Cancellation Rate by Distribution Channel
This analysis compares cancellation rates across various distribution channels, highlighting which channels have higher or lower booking reliability. Identifying channels with elevated cancellation rates enables hotels to develop targeted strategies to improve booking stability, such as adjusting booking policies or enhancing customer engagement for riskier channels.
 

Conclusion
This comprehensive analysis of hotel booking data offers valuable insights into guest behavior, revenue patterns, and operational challenges in the hospitality sector. Key findings include:
•	City Hotels generally exhibit lower cancellation rates and more stable booking trends compared to Resort Hotels, likely due to their business-oriented clientele.
•	Customer type matters—Contract and Group bookings show near-perfect reliability, whereas Transient guests contribute to the highest cancellation rates, indicating the need for more flexible or targeted retention strategies.
•	Seasonality plays a significant role in booking volume, with peak demand in November and low activity during early spring months.
•	Booking trends over time show sharp fluctuations, helping identify high-demand periods and aiding resource planning.
•	Revenue analysis reveals that cancellations significantly impact overall earnings, and certain market segments and distribution channels are consistently more profitable.
•	ADR (Average Daily Rate) distribution shows most bookings are concentrated in mid-range pricing, suggesting optimal pricing strategies should target those segments.
•	Lead time and cancellation correlation shows that longer lead times tend to correlate with higher cancellation rates.
•	Geographic insights reveal that a few countries dominate booking volume, suggesting regional marketing could yield high returns.
•	Distribution channels vary in both volume and reliability, with some channels prone to higher cancellation risks, guiding hotels to prioritize effective and stable channels.
Together, these insights support more data-driven decision-making for pricing, marketing, resource allocation, and customer engagement strategies in the hotel industry.

