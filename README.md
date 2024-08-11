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
Sales by country

<img width="278" alt="Screenshot 2024-08-11 at 10 06 15 PM" src="https://github.com/user-attachments/assets/c18819d5-9def-4487-8377-78244099370e">

Sales by Month

<img width="368" alt="Screenshot 2024-08-11 at 6 47 02 PM" src="https://github.com/user-attachments/assets/41a8ecbe-0d51-485f-9b9f-f99cdda73139">

Sales by Roast Type

<img width="278" alt="Screenshot 2024-08-11 at 10 07 48 PM" src="https://github.com/user-attachments/assets/7619b7de-5fb9-4f2d-a910-218587d9153e">

Sales by Coffee Type

<img width="278" alt="Screenshot 2024-08-11 at 10 08 19 PM" src="https://github.com/user-attachments/assets/2a0eec20-da3d-4a7e-946b-f29aee575e58">

Sales on Weekends or Weekdays

<img width="278" alt="Screenshot 2024-08-11 at 10 09 09 PM" src="https://github.com/user-attachments/assets/25dc9877-2bba-44b9-b6f5-0cf27ddb30e3">

### Data Visualization
Please find the dashboard <here>
<img width="1575" alt="Screenshot 2024-08-11 at 8 15 04 PM" src="https://github.com/user-attachments/assets/a137bdae-2c40-4d32-99b7-45219a60531e">

### Key Findings
Sales by Country:
The United States leads with the highest sales, totaling *$35,638.89*, Ireland follows with sales of *$6,696.87* and the UK has the lowest recorded sales among the listed countries, amounting to *$2,798.51*.
The Grand Total sales across all countries sum up to *$45,134.26.*
This would indicate that there is a need for *onboarding marketing initiatives* in the UK and Ireland where as *retention and loyalty card marketing initiatives* would be beneficial in the US. 

Sales by Month:
January to March ( and June )  has the highest number of sales. This would indicate that people aren't purchasing as much in the summer months. Summer drinks made with coffee can be marketed along with discounts. 

Coffee and Roast type
Lightly roasted, Excelsa Coffee is the most popular choice. 

Sales are more during the weekdays than the weekends. Weekend offers can be implemented. 



