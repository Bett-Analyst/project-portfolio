E-COMMERCE FOR A LONDON BASED COMPANY

Dashboard Link

PROBLEM STATEMENT

This dashboard helps the London based online retail business understand the customer trends based on their purchase bahavior and purchae decision 
making in order to improve customer satisfaction and guarantee customer loyalty. 
Understanding the trends of sales will enable the business understand the months that will need more stock in store. 
Finding the most frequrntly purchased product would also ensure that they plan ahead depending on what is left on the stock.
Customer purchase will also determine the consumption patterns of each individual customer.
The customer base was also divided into different segments - Countrywise. It is also nobble to understand the profitability of each segment.
The customer satisfation was based on  their order cancelation rate, and since there were about 23% of cancelation rates the business should work on 
ensureing that stock is in contsant supply since it was the major reason for the customer not completeing the purchase. In this case the project 
establsihed the following questions to undertake to achevie the desired end result:

1.	How was the sales trend over the months?
2.	What are the most frequently purchased products?
3.	How many products does the customer purchase in each transaction?
4.	What are the most profitable segment customers?

STEPS TAKEN

1. I first cleaned the data in Excel. It was discovered that the date column had dates in text form which other subsequent functions could not read it including SQL database and Power Bi.
   I did this by ensuring date column was in the correct format.
3. I then checked for blanks in the data and other irregularities that would bring discrepancy in the data.
4. I then loaded the data into postgresql database for analysis. 

5. The first step was to find the sales trend over the months. The querry bellow enables me to pull out the data
   grouped in months to find the total sales from th sales transaction table.

         SELECT 
        	DATE_TRUNC('month', purchase_date) AS mnth,
        	SUM(sales) AS total_sales
        FROM sales_transactions
        GROUP BY mnth
        ORDER BY mnth DESC
         LIMIT 10;

The results was dowloaded as CSV file as shown in the image blow.

![image](https://github.com/user-attachments/assets/24fd6f54-6e19-4836-a49b-39400f995986)


   The second step was to find the most frequently purchased product. The following querry ensured 
   that the top 10 most purchased products were listed and I dowloaded the data as a CSV file as show. 

           SELECT transaction_no, customer_no, COUNT(product_no) AS Products_purchased
        FROM sales_transactions
        GROUP BY transaction_no, customer_no
        ORDER BY products_purchased DESC;  	
![image](https://github.com/user-attachments/assets/0e5af239-47ed-426e-8e4a-a8fdb33d2ad8)

The third step was to find the total number of products a customer purchased in each transaction. 

    SELECT transaction_no, customer_no, COUNT(product_no) AS Products_purchased
    FROM sales_transactions
    GROUP BY transaction_no, customer_no
    ORDER BY products_purchased DESC
    LIMIT 10;

The result was limited to the top 10 most purchased products as shown in the downloaded CSV file. 

		
![image](https://github.com/user-attachments/assets/8896d377-b3bc-4401-a14c-61f559093d55)

The last step was to check on the profitability of each customer segment. 

    SELECT country, SUM(sales)AS total_revenue
    FROM sales_transactions
    GROUP BY country 
    ORDER BY total_revenue DESC
    LIMIT 10;

![image](https://github.com/user-attachments/assets/1c21d6b7-6ff3-4ee1-9dd0-433d51a23b44)

6. The next step was to upload the data into power BI for visualization and analysis.



