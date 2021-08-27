# Kickstarting with Excel

## Overview of Project

### The purpose of this analysis was to investigate how different Kickstarter fuding campaigns for theatrical plays fared with respect to their launch date and funding goals. Further, the hope of the analysis was to provide feedback to Louise about her own play's fundraising goals and how it compared to others.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
Because fundraising activities take place throughout the year, the first analysis performed was to look at how Kickstarter compaigns fared based on their launch (start) dates. Starting with the data provided, the first challenge was simply to convert the launch dates from Epoch Time (number of seconds from January 1, 1970) to a more typical human readable (MM/DD/YYYY) format. To do this, I took the Epoch Time (which is in seconds) and converted it into days. Then I took this days count and added it to January 1, 1970. By doing this, I arrived at the converted MM/DD/YYYY format I was looking for. From there, I was able to extract just the year using Excel's `Year()` function. After performing these steps, I was at the proper data specification I needed to begin my analysis of Outcomes Based on Launch Date using a Pivot Table and Pivot Chart.

Example Excel code for the Epoch Time conversion: `(((J2/60)/60)/24)+DATE(1970,1,1)`

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/89284280/130330965-f3d12aec-77ee-49e6-bae7-c8fd3fc16fee.png)

### Analysis of Outcomes Based on Goals
The next analysis invovled looking at the count and percentage of successful, failed and canceled compaigns for plays based on their funding goals. The purpose here was to analyze the impacts of overall funding goal on the compaign. The strategy was to place each successful, failed or canceled play compaign in a funding goal bucket/bin, each separated by about $5,000. Then, I used the `=COUNTIFS()` Excel function to count the number of plays by funding bin who were either successful, failed or canceled. Once those counts were determined, I then calculated a percentage of success, failure or cancelation. These values were then placed on a line graph with those compaigns with the lowest goals (< $1,000) on the left side of the X-axis to those campaigns with the highest (>= $50,000) goals on the right side of the X-axis.

Exampel Excel code using COUNTIFS: `=COUNTIFS(Kickstarter!R:R,"plays",Kickstarter!F:F,"failed",Kickstarter!D:D,">=" &A3,Kickstarter!D:D,"<" &B3)`

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/89284280/130330971-a42a61dd-84fe-4736-848e-a3aaf6996c55.png)

### Challenges and Difficulties Encountered
As mentioned above, the first challenge was to convert the Epoch Time into something more human readable. To do this, I converted the seconds since Jan 1 1970 into number of days. I then added this day count to Jan 1, 1970 using the Excel `DATE()` function to arrive at the MM/DD/YYYY that I was looking for.

Lastly, because I needed to determine counts of plays based on campaign outcome, I had to create a separate table of bin ranges and use `COUNTIFS()` to populate it. This table was then used for the Outcome Based on Goal analysis.

## Results

1. What are two conclusions you can draw about the Outcomes based on Launch Date?
   - There is a clear seasonality to when most of the successful campaigns occur. May through July saw the most success (in volume) compared to other months. As a result, a Luanch Date of May, June or July is where most of the successful outcomes are found.
   - Unlike the seasonality for successful campaigns, Failed and Canceled campaigns had much less variability month to month. As a result, the month of the Launch Date did not seem to impact Failure or Cancelation rates much.

2. What can you conclude about the Outcomes based on Goals?
   - Lower campaign goals ($15,000 or less) saw relatively higher rates of success. As the campaign goals increased, the rate of failre increased.
   - The above conclusion holds true in all goal bin ranges except for $35,000 to $45,000. Between these funding goals, the percent that were successful out performed those that failed. 
3. What are some limitations of this dataset?
   - Simply looking at campaigns goal vs pledges does not expalin the entire story of why a Kickstarter was successful or not. Other considerations that should be included are:
     - Marketing support: social, word-of-mouth, etc.
     - What city or even specific location (ex: theater) would be hosting it. Local support in the arts performances goes a long way.
     - Also, who is managing and putting on the performance can have an impact on it's success.
4. What are some other possible tables and/or graphs that we could create?
   - Success rate by country (table and a Column/Bar Chart). This chart would provide insight into success rate by country. Perhaps it's better to host a performance in the U.S. versus France.
   - Number of days between Launch and Deadline. Does the number of days a campaign is open have an impact on success? This can be shown in a line graph or bar chart.



