
# Average Sales Analysis-Dashboard

### Dashboard Link : https://app.powerbi.com/view?r=eyJrIjoiOGQxZmVhZTQtNGE4OS00Mjk3LThhOTQtNjdhZGEwM2IwZTEwIiwidCI6IjM4ZjYyOTI2LTc1NTktNGFlZi04NGFlLWNiNWUxNzI0MDZmYiJ9

## Description

This dashboard helps us analyze and compare the average sales of different products (one at a time or many) between 2 distinct time periods, with user-adjustable periods.This dashboard also gives us the difference between the total sales amount and the average sales of the 2 time frames.

The excel data file used is uploaded. Its description goes as :

#### Dimensions:
- Year - Month
- Product Line
- Part Number
#### Facts:
- Quantity (Volume)
- Net Sale Amt (price)


### Steps followed 

- Step 1 : In the given Excel file add another date column Date2 with same values of Date1
- Step 2 : Load the data into Power BI Desktop. 
- Step 3 : A new table named Initial_1 was created containing distinct values of Date1 column with help of the following DAX expression: 
        
        Initial_1 = DISTINCT('Data'[Date1])        
- Step 4 : Similarly create another table named Initial_2 for Date2. The DAX expression will be:

        Initial_2 = DISTINCT('Data'[Date2])
  Snap of the tables created should look like :
  ![Initial_1 Table](https://github.com/snigdha-a20/Power-BI/assets/125685896/77846ffc-dbb8-4aa9-a6e0-a04ac0220754)
 
- Step 5 : For calculating the Total Amounts for the time frames we create two measures using the DAX expressions below 

        Total Amount 1 = CALCULATE(SUM('Data'[Net Sale Amt]),'Data'[Date1] in VALUES(Initial_1[Date1]))
        Total Amount 2 = CALCULATE(SUM('Data'[Net Sale Amt]),'Data'[Date2] in VALUES(Initial_2[Date2]))
- Step 6 : For calculating the total total quantity for the time frames two measures were created using the DAX expressions below
    
        Total Qty 1 = CALCULATE(SUM('Data'[Quantity Sold]),'Data'[Date1] in VALUES(Initial_1[Date1]))
        Total Qty 2 = CALCULATE(SUM('Data'[Quantity Sold]),'Data'[Date2] in VALUES(Initial_2[Date2]))       

- Step 7 : For Average Sales i.e., Total Sales/ Total Quantity for each month two measures were created for each time frame respectfully using 

        Avg Amount 1 = CALCULATE([Total Amount 1]/[Total Qty 1],'Data'[Date1] in VALUES(Initial_1[Date1]))
        Avg Amount 2 = CALCULATE([Total Amount 2]/[Total Qty 2],'Data'[Date2] in VALUES(Initial_2[Date2]))

- Step 8 : Two Clustered Column and Line charts were added to visualise the Data of different products month-wise and product-wise
![Charts](https://github.com/snigdha-a20/Average-Sales-Analysis/assets/125685896/886524f3-122a-48f9-954c-497f84e6a5a4)


- Step 9 : Two card visuals were added to the canvas, representing the Total quantity, Total sales and Average sales of different products for the two time frames.
![Cards](https://github.com/snigdha-a20/Average-Sales-Analysis/assets/125685896/27018254-4658-470c-9c21-e5ce8eff3936)



- Step 10 : A slider is added to each time frame for the user to adjust the time frames as required.
![Date Slider](https://github.com/snigdha-a20/Average-Sales-Analysis/assets/125685896/ff424077-8e1a-4599-b775-c1148a52510b)


- Step 11 : For Difference in Sales three measures were created for Sales Amount Difference, Avg Amount Difference and Difference in Quantity respectfully using the following DAX expressions

        Sales Amount Diff = [Total Amount 1]-[Total Amount 2]
        Diff Average Amount = [Avg Amount 1]-[Avg Amount 2]
        Diff Quantity = [Total_Qty_1]-[Total_Qty_2]

- Step 12 : A card was added to show the Difference in Sales Analysis
![Diff](https://github.com/snigdha-a20/Average-Sales-Analysis/assets/125685896/87e9f686-24d3-42ab-9678-a8211c1abe76)

- Step 13 : To analyze the sales of different products one or all at a time a slicer was added for product seperation.
![Product Slicer](https://github.com/snigdha-a20/Average-Sales-Analysis/assets/125685896/ae07527c-c6c8-46a1-9d9e-c55b6078c0da)


Upon following the above steps we have been able to create a dashboard that fits our requirement. The Dashboard is as shown below.

### Dashboard Snapshot :
![Dashboard snapshot](https://github.com/snigdha-a20/Average-Sales-Analysis/assets/125685896/093cda72-f8cf-47bb-8816-3efd728ff5cb)



# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.
With this dashboard one can draw the following Insights :

The Average Sales of different products can be compared across different time frames month-wise and product-wise and also obtain the difference between the sales of the time frames.

