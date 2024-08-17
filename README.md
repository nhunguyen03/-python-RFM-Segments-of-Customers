## OVERVIEW
An online retailer needs to **offer target promotions**. To optimize marketing and sales strategies, the company uses RFM (Recency, Frequency, Monetary) analysis to segment customer. This segmentation helps tailor strategies for different customer groups. 

For instance, loyal customers (Champions) can receive exclusive offers, potential loyalists can be targeted with promotions, and at-risk customers can be re-engaged with reminders and special offers. New customers can be welcomed with discounts, and inactive customers can be reactivated with significant promotions.

## DETAIL
- ### **Dataset:** captures transactional information from a retail business, providing detailed records of sales and customer interactions.
  + InvoiceNo: a unique identifier for each transaction or invoice.
  + StockCode: a unique identifier for each product.
  + Description: a textual description of the product being sold.
  + Quantity: the number of units of the product sold in the transaction.
  + InvoiceDate: the date and time when the transaction was recorded.
  + UnitPrice:  price of a single unit.
  + CustomerID: a unique identifier for the customer who made the purchase.
  + Country: country where the transaction took place.
![image](https://github.com/user-attachments/assets/e81e43f5-4cd7-4843-ba4b-d8cd27f1898c)

- ### **EDA: correct datatype, no missing values**
  After checking missing values, incorrect data, duplicates, outlier; we have **6 problems** below:  
  ![image](https://github.com/user-attachments/assets/d52b54de-ef4d-41ca-9db5-e4dded36c54b)

  Then fixing these problems:
  ![image](https://github.com/user-attachments/assets/68e930e2-8a70-4b4b-978e-43fd8d839ce2)

  I want to clearify the way to fill mising values in CustomerID. There are 2 ways:
    + Solution 1: based on InvoiceNo, forward fill CustomerID (1 InvoiceNo associates to only 1 CustomerID)
    + Solution 2: fill fake CustomerID (we assump that null value in CustomerID is one-time visitor - bought once => fake CustomerID only appear once)
    After using solution 1, no missing values are replaced and we should not remove missing values because the number of that is too large **(Data is the New Gold)**. Therefore, using solution 2 to handle null values.

- ### **Segmentation: RFM method**
Because I do not have sense in this field, dataset is divided into 5 parts by quintile (basic method). 
5 is the highest score corresponding to positive things, in contrast 1 is the lowest score corresponding to negative things.

  + **Recency**: Calculate the number of days since the last purchase for each customer. The **most recent buyers** get a score of 5, while the least recent get a score of 1.
  + **Frequency**: Count the total number of purchases each customer has made. The **most frequent buyers** get a score of 5, while the least frequent get a score of 1.
  + **Monetary**: Sum the total amount spent by each customer. The **highest spenders** get a score of 5, while the lowest spenders get a score of 1.

  + **RFM segmentation model**

  ![Customer Segmentation - RFM method](assets/segment_RFM.png)

- ### **Conclusion**
  - **QUANTITY & MONETARY**
    + **Champions**: 1200 customers, highest avg spending (5000), 60% total revenue.
    + **New Customers, Need Attention, At Risk, Loyal**: more customer, more spending, 5-9% total revenue (except for New Customer - 2% total revenue).
    + **Potential Loyalist, Lost customer, About to Sleep, Hibernating**: 600-800 customers, low spending < 500, less than 2% total revenue.
    + **Promising, Cannot Lose Them**: 200-400 customers, quite high spending (2000), 5-9% total revenue.
   
  - **FREQUENCY & RECENCY**
    + **Champions**: median 7 purchases, recent orders
    + **Cannot Lose Them, Lost Customer**: median 1 purchases, no orders in 1 year
    + **Hibernating, About To Sleep, At Risk**: median 1-2 purchases, no orders in 5-7 months
    + **New Customer, Potential Loyalist, Promising, Need Attention, Loyal**: median 1-3 purchases, no orders in 1-3 months
![Customer Segmentation - RFM method](assets/result_segmen_RFM.png)

![image](https://github.com/user-attachments/assets/4f56251a-6284-401e-83c2-654bf55782ae)

![image](https://github.com/user-attachments/assets/003f40f6-f4f5-4c9d-b045-73ff4548f621)

- ### **Strategy**
  + **Champions**
  + **Loyal**
  + **Potential Loyalist**
  + **New Customers**
  + **Promising**
  + **Need Attention**
  + **About To Sleep**
  + **At Risk**
  + **Cannot Lose Them**
  + **Hibernating Customers**
  + **Lost Customers**
