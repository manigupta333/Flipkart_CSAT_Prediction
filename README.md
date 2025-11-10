# Flipkart_CSAT_Prediction
This project develops a machine learning solution to predict Customer Satisfaction (CSAT) scores for Flipkart's customer support interactions.

# THE PROBLEM
Flipkart handles thousands of customer support interactions daily - calls, chats, emails about orders, returns, and product issues. After each interaction, customers are asked to rate their satisfaction on a scale of 1 to 5 stars.
Here's the problem: Only 33% of customers actually complete the satisfaction survey. That means for 67% of interactions, Flipkart has no idea whether customers are happy or frustrated.

# What I Did
I built a machine learning model that predicts how satisfied customers will be with Flipkart's support service. Instead of waiting days for survey responses, this model predicts satisfaction scores instantly for every customer interaction.
My solution predicts satisfaction for everyone - not just survey respondents. This means supervisors can immediately call back customers who are likely dissatisfied, before they leave negative reviews or stop shopping at Flipkart.

# The Data
I worked with 85,907 real customer interactions from August 2023. Each interaction had information like:

- How long customers waited for a response
- Which agent helped them
- What time of day it was
- What the issue was about
- What customers wrote in their feedback

The most interesting finding? Response time matters more than anything else. Customers who get help within 5 minutes are much more likely to be satisfied.

# What I Found Out
After analyzing the data through charts and statistical tests, here's what I discovered:

1. Speed wins: The faster agents respond, the happier customers are. Every extra minute of waiting drops satisfaction by 0.1 stars.

2. Experience counts: New agents (still in training) get an average rating of 3.8 stars. Experienced agents (working over 3 months) get 4.4 stars. That's a huge difference.

3. Sentiment matters: When I analyzed what customers wrote using AI, I found that positive language strongly predicted high ratings, and negative language predicted low ratings.

4. Timing patterns: Some hours of the day (like 10 AM to noon) had slightly lower satisfaction scores, probably because that's when call volumes are highest and agents are stretched thin.

5. Category differences: Returns and cancellations had the lowest satisfaction scores (3.7 average), while simple product questions had the highest (4.2 average).

# How I Built the Model
I tested three different machine learning approaches:

Logistic Regression: A simple model that got 78% accuracy. Not bad, but not great either.

Gradient Boosting: A more complex model that reached 87% accuracy. Better, but slow to run.

Random Forest: This was the winner. Think of it like asking 200 different experts for their opinion and taking a vote. Each expert (decision tree) looks at the data slightly differently, so together they make better predictions than any single expert could. This model hit 92% accuracy.

I spent time tuning the Random Forest model - adjusting settings like how many trees to use and how deep each tree should go. The final version predicts correctly 92 times out of 100, which is really good for this kind of problem.

# How It Actually Works
Here's what happens when a customer contacts Flipkart support:

Step 1: The system records everything - response time, agent name, issue type, time of day, etc.

Step 2: If the customer leaves written feedback, I use natural language processing to figure out if their tone is positive or negative.

Step 3: All this information goes into the model.

Step 4: The model looks at patterns it learned from 57,000 past interactions and predicts: "This customer will probably give us 5 stars" or "This customer might only give us 2 stars."

Step 5: If the prediction is low (3 stars or below), the system can alert a supervisor to call the customer back immediately.

The whole process takes milliseconds, so it happens in real-time.

What Flipkart Should Do With This
Based on my analysis, I'm recommending three immediate actions:

First: Set up automatic alerts. When the model predicts someone will give a low rating, send an immediate notification to supervisors. Let them reach out before the customer gets more frustrated. This could recover 1 out of 4 at-risk customers.

Second: Create a 10-minute response time target. The data clearly shows that quick responses drive satisfaction. Right now, half of customers wait longer than 5 minutes. Getting that average down would boost satisfaction scores across the board.

Third: Improve new agent training. There's a big gap between new and experienced agents. Pair every new hire with a top performer for their first 90 days. Use insights from the model to teach them what actually makes customers happy.

For the long term, Flipkart should keep feeding new data into the model every month so it keeps learning. They could also add more information like customer purchase history and demographics to make predictions even more accurate.

The Bottom Line
This project shows that we can predict customer satisfaction with 92% accuracy using information that's available the moment each interaction happens. Instead of knowing how 33% of customers feel (those who fill out surveys), Flipkart can now predict how 100% of customers feel.

The business impact is real: fewer angry customers, better agent training, smarter staffing decisions, and ultimately, more people shopping at Flipkart because they trust the customer service.

I've saved the trained model as a file that Flipkart can plug directly into their systems. All the code is documented and ready to go.

What Could Be Better
No project is perfect. Here are things I'd improve if I had more time:

The data only covers one month (August), so it might miss seasonal patterns. Customer feedback was missing 67% of the time, which limited how much I could learn from text analysis. And the model occasionally confuses ratings that are close together (like 4 versus 5 stars), though that's not a huge problem for the business use case.

If I continue this project, I'd add more advanced language understanding (using models like BERT), include customer history data, and set up automated retraining so the model stays accurate as customer behavior changes.

Technical Details (For the Curious)
Programming: Python with pandas, scikit-learn, and TextBlob

Best Model: Random Forest with 200 trees, maximum depth of 20

Train/Test Split: 70% training, 30% testing

Feature Count: 50 features after encoding categorical variables

Processing Time: Model trains in about 3 minutes, predicts in milliseconds

This project gave me hands-on experience with the entire data science workflow - from messy real-world data to a deployed solution that can actually help a business. It's not just about algorithms and accuracy percentages; it's about understanding what customers need and using data to deliver better service.
