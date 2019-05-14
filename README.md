## data_bootcamp_final_project_2019
Final project for Data Bootcamp 2019

This project was completed by **Motoi Oyane** in partial fulfilment of ECON-UB.0232, Data Bootcamp, Spring 2019. I certify that the NYU Stern Honor Code applies to this project. In particular I have:

Clearly acknowledged the work and efforts of others when submitting written work as our own. The incorporation of the work of others-including but not limited to their ideas, data, creative expression, and direct quotations (which should be designated with quotation marks), or paraphrasing thereof- has been fully and appropriately referenced using notations both in the text and the bibliography.

And I understand that:

Submitting the same or substantially similar work in multiple courses, either in the same semester or in a difference semester, without the express approval of all instructors is strictly forbiden.

I acknowledged that a failure to abide by NYU Stern Honor Code will result in a failing grade for the project and course.

## Project Description

### Abstract

This project will study how a company's pre-IPO status (Max Valuation, Total Funding, Exit Round, Operating Sector) affect the stock price behavior after IPO. I will specifically target companies that were VC-backed, head quartered in United States (US), and exited through IPO. This analysis is especially relevent in 2019 as we are anticipating many Unicorns to go public, after Lyft's poor and Beyond Meat's strong market debut. 


### Process Outline

The key elements of the project if the use of [CBInsight's Data Collection](https://www.cbinsights.com/search/deals) that provides access to the companies that fit the criteria above and [Alpha Vantage's API](https://www.alphavantage.co/) that provides access to the daily stock prices of each company. The following is the description of the dataset that I will obtain and will need.

- **pre-IPO data from CBInsight Dataset**: I will obtain the data set from [https://www.cbinsights.com/search/deals](https://www.cbinsights.com/search/deals) where I will filter the search by Geography (United States), Company Status (IPO/went public), and Backing (Only show VC-backed companies). The data will be exported in csv format, which I will import on jupyter as a DataFrame. I will clean this data by removing irrelavent data attributes for each companies such as "# of Twitter Followers", "Min Valuation", "URL" (shown below in Data Report), removing companies with insufficient information, and by keeping companies that were funded in Seed and/or Series A~I. 
- **ticker from Yahoo Finance**: After cleaning the CBInsight Dataset, I will export the DataFrame and manually obtain all of the companies' ticker from [https://finance.yahoo.com/](https://finance.yahoo.com/).
- **stock price from Alpha Vantage API**: Then, I will re-import the data as csv and access the API for Alpha Vantage (using a free API key that they issue: [https://www.alphavantage.co/](https://www.alphavantage.co/)) to download the daily share price for each company. 

After the collecting the full data, I anticipte that the project will have three sections:

1. **Analyzing the data** - Making a new dataframe with: ticker, company name, sector, exit round, IPO date, pre-IPO max valuation, total funding, cumulative return after 1-12 months

2. **Grouping the data** - Grouping the companies:

 - ***exit round***: Early Stage (Seed, Series A, B), Growth Stage (Series C-D), Late Stage (Series E-I)
 - ***total funding***: <50m,50m~100m,100m~200m,200~300m, >300M
 - ***pre-IPO max valuation***: <100m,100m~500m,500m~1bn,1bn~10bn,>10bn
 - ***Sectors***
 
 
3. **Plotting the data** - Plotting the four sets of graphs:

 - Line Graph: ***cumulative return vs time since IPO*** of each of the exit round groups
 - Line Graph: ***cumulative return vs time since IPO*** of each of the total funding groups
 - Line Graph: ***cumulative return vs time since IPO*** of each of the pre-IPO max valuation
 - Line Graph: ***cumulative return vs time since IPO*** of each of the sectors
  
### Hypothesis 

- Companies that exited in the Growth Stage will have the highest ***cumulative returns vs time since IPO***
- There will be a positive correlation between total funding the ***cumulative return vs time since IPO***
- There will be a positive correlation between pre-IPO max valuation the ***cumulative return vs time since IPO***
- Companies in the Healthcare sector will have the highest ***cumulative return vs time since IPO***

### Limitations

There are few potential limitations to the process and the outcome:

- There is a manual process of gathering ticker names, which limits the efficiency and flexibility of the project. This is due to the data output of the CBInsights' dataset because the company names are not given as the full legal name (e.g. Facebook, Inc. will be given as Facebook) and there are no available APIs that allow abbreviated names to be matched with official tickers to be downloaded.

- Through my investigation of th data I found out that Alpha Vantage did not have the stock price because these companies were delisted from the market, so I will need to remove them from my investigation.

- Through my investigation of th data I found out that Alpha Vantage only had the daily stock data from 1998-01-02 so I have to adjust my time-series analysis accordingly.

- The groupings/graphs may not present an accurate representation of the stock price behavior because within each group there are companies that:
   - went private, acquired or merged after a period of time so it may be not sensible to group these companies together with ones that are still public.
   - went public too recently so not all cumulative returns will not be available and it may not be sensible to compare the statistics of these companies to those that have been public for a logner period of time.
