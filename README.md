## Sales Analysis using Excel and Tableau
### Business Task
Analyze the sales data of our coffee company to understand trends and guide future marketing ventures, ultimately aiming to increase sales and customer engagement.
### Data Source
The dataset used for this analysis is sourced from a repository curated by the YouTube creator Mo Chen, known for his educational content on data analysis and machine learning. This comprehensive dataset comprises three CSV files, each containing valuable information for detailed examination.
### Data Integrity 
- Reliability ; The data source is unknown but it is well suited for practice. 
- Comprehensive ; The data is has comprehensive records of customer, orders and product information which will be helpful in deriving meaningful insights.
### Data Processing
Populate *Customer Name, Email, Country, City, Loyalty card* in orders using XLOOKUP function.

```
=XLOOKUP(F2,customers!$A$1:$A$1001,customers!$B$1:$B$1001,,0)
=XLOOKUP(F2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)
=XLOOKUP(F2,customers!$A$1:$A$1001,customers!$G$1:$G$1001,,0)
=XLOOKUP(F2,customers!$A$1:$A$1001,customers!$F$1:$F$1001,,0)
=XLOOKUP(orders!$F2,customers!$A$1:$A$1001,customers!$I$1:$I$1001,,0)
```
I noticed that the email column had a lot of missing values and they returned as zero, so I modified the function with IF function.
```
=IF(XLOOKUP(F2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)=0,"",XLOOKUP(F2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0))
```
Populate *Coffee Type, Roast Type, Size, Unit Price* in orders using INDEX function.
```
=INDEX(products!$A$1:$G$49,MATCH(orders!$G2,products!$A$1:$A$49,0),MATCH(orders!M$1,products!$A$1:$G$1,0))
```
Calculating the sales by simple multiplication.
```
=P2*H2
```
Formating the Coffee Type and Roast Type from short to full forms using the IF function.
```
=IF(M2="Rob","Robusta",IF(M2="Exc","Excelsa",IF(M2="Ara","Arabica",IF(M2="Lib","Librica",""))))
=IF(N2="L","Light",IF(N2="M","Medium",IF(N2="D","Dark")))
```
I prefer the date to be in the *dd-mmmm-yyyy* format, so I am chnaging the format using the formating tool.
```
Format Cells > Custom > dd-mmmm-yyyy
```
Extracting the month of sale to track sales trends throughout the year using the TEXT function.
```
=TEXT(B2,"mmmm")
```
I want to check if there is a difference in sales during the weekdays and weekends. For this I need to extract the day using the TEXT function and use the IF function to convert it to weekends or weekdays. 
```
=TEXT(B3,"dddd")
=IF(D2="Saturday","Weekend",IF(D2="Sunday","Weekend","Weekday"))
```
Finally I am going to convert the size into Kg and the prices into $ using the formating tool.
```
Format Cells > Custom > General "kg"
Format Cells > Currency
```
Check for duplicates and convert to table. 
### Data Analysing 

[Uploading Coffee_sales_analysis_dashboard.twb…]()


