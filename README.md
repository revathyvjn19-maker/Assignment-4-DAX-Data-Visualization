# Assignment-4-DAX-Data-Visualization
DAX &amp; Data Visualization
-	Created relationship with tables
-	Date format changed in tables

# 1.	CALCULATED COLUMNS

1)Create a Calculated Column for 'Category Type

**Category Type = ('Order Details'[Category])&"-"&('Order Details'[Sub-Category])**

2)	Calculate Revenue per Order in Order Details Table

**Revenue = 'Order Details'[Amount]*'Order Details'[Quantity]**

3)	Create a Calculated Column to Categorize Sales

**Sales Category = IF('Order Details'[Amount]>AVERAGE('Order Details'[Amount]),"Above Average","Below Average")**

# 2.	Calculated Measures:

1)	Calculate Order Count

**Total No of orders = DISTINCTCOUNT('Order Details'[Order ID])**

2)	Calculate Average Profit in Delhi

**Average Profit in Delhi = CALCULATE(AVERAGE('Order Details'[Profit]),'List of Orders'[City]="Delhi")**

3)	Calculate Year-to-Date (YTD) Sales

Created new Date table And Created Relationship 

**Date Table = ADDCOLUMNS(CALENDAR(MIN('List of Orders'[Order Date]),MAX('List of Orders'[Order Date])),"Year",YEAR([Date]),"month Number",MONTH([Date]),"month name",FORMAT([Date],"MMM"),"Day",DAY([DATE]))**

Calculated total sales & sales YTD
 
**Total sales = Total Sales = SUM('Order Details'[Amount])**

**Sales YTD = TOTALYTD('Order Details'[Total Sales],'Date'[Date])**

3.	Data Visualization:

1)	Sales Target Achievement by Category:

Find Total sales and total target
Insert clustered column chart
X axis – category
Y axis Sales & target


2)	Max Profit Margin by Sub-Category:

Find Total sales and Total profit and Profit margin and insert donut chart
Profit Margin = 'Order Details'[Total Profit]/'Order Details'[Total Sales]

Legend =Sub category
Values = Profit margin

3)	Monthly Sales Trend:
Calculate Total sales and insert line chart
Y axis = Total sale 
X Axis = Month and Year

4)	Comparison of Profit and Quantity by Sub-Category:

Find total quantity, total profit and insert values in scatter chart. 
 Total Quantity = SUM('Order Details'[Quantity])

X Axis = Total Quantity
Y Axis = Total Profit
Values = Sub category
Legend = Category


5)	Comparison of Total Sales Amount and Target
Unable to find the Multi row card in my visualizations
Calculated Total sales, total target, Minimum target and added Card visuals

Minimum Target = MIN('Sales target'[Target])

Values – Total sales, Total Target , Minimum Target
Category - Category


6)	Sales Performance Matrix:

Calculate Total sales, Total Target, Variance and Achievement % and added Matrix

Variance = 'Order Details'[Total Sales]-'Sales target'[Total Target]
Achievement %= ('Order Details'[Total Sales]/'Sales target'[Total Target])*100

Rows =Date – Year and Month
Columns =Category and Sub category
Values = Total sales, Total target, Variance, Achievement %

7)	Geographic Sales Analysis

Calculate total sales , added new column “Location”  in List orders table and Insert Map 

Location = 'List of Orders'[City]&","&'List of Orders'[State]&",India"

Location – Location 
Bubble size – Total sales
Tooltips – Total sales , State 

8)	Sales Distribution by Sub-Category:

Calculate Total sales and added Treemap
Category – Sub Category
Details – Category
Values – Total sales 

9)	Order Count Analysis by State
Calculate order count and created a funnel chart

Total No of orders = DISTINCTCOUNT('Order Details'[Order ID])
Category – state
Values – Total no of order

