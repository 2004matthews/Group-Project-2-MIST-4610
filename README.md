# Group #6 Project 2 MIST4610
Chemicals in California 
Tableau Analysis

# Team Members:
1. Alexandra DiClemente, @akd27602
2. Chris Johnson, @cjohns417
3. Mckenna Isenberg, @mckennaisen
4. Kennedy Johnson, @kennedyrjohnson
5. Charlie Matthews, @2004matthews

# Dataset Description:
We have obtained our database from the US Data gov website at https://catalog.data.gov/dataset. 

The California Safe Cosmetics Program (CSCP), under the California Department of Public Health (CDPH), collects data on products sold in California that contain ingredients linked to cancer, birth defects, or reproductive harm. Companies with over $1M in annual sales and operating since 2007 must report products with these chemicals. The data is aimed to help consumers make informed decisions about the products they use or are considering purchasing. Also, regulatory agencies may use this data to analyze trends in company's use of chemicals in cosmetics, monitoring a company's compliance with the Safe Cosmetics Act overtime.

The dataset includes product labels, brands, manufacturers, categories, reported chemical ingredients (with CAS#), the number of chemicals per product, and dates of reporting or reformulation. It aims to inform the public about potentially hazardous cosmetics but may lack full coverage due to underreporting by companies. 

Our database showcases chemicals in cosmetics primarily. It shows the specific product name, company name (Ex- Glover’s medicated Shampoo made by J. Strickland & Co.)
, product category (Ex- Hair Care products), chemical used (Ex- Distillates (coal tar)), and chemical count based on a scale from 0-2 (Ex-2)). Additionally, it provides the initial date imported and most recent dated (Ex-7/1/2009, 7/1/2009).

The data dimensions consists of rows and columns. There are records for individual cosmetic/personal care products, where each row represents a single product or a product formulation. There are multiple columns in the dataset, each containing many attributes of each product.


![Screenshot 2024-11-22 125937](https://github.com/user-attachments/assets/e025501d-ad77-4844-b72c-62051b11aec5)


![Screenshot 2024-11-22 130006](https://github.com/user-attachments/assets/8d6f03ed-ff5a-414b-b7b1-9747371ff9fa)


![Screenshot 2024-11-22 130024](https://github.com/user-attachments/assets/9461c6fd-e7ac-4e7d-b310-d13f229972be)


![Screenshot 2024-11-22 130041](https://github.com/user-attachments/assets/7317de86-832c-4cb4-970a-947a9ac594bc)



# Analysis Question #1:
Which companies have the highest number of products containing carcinogenic ingredients with a rating of at least 1A? 
 - A rating of at least 1A  refers to the classification of carcinogenic ingredients. 1A is considered known to have carcinogenic potential for humans, based on evidence from human studies, meaning there is sufficient data to conclude it causes cancer in people.
 - By filtering products by CAS number, we can see products with carcinogenic ingredients rated 1A or higher.
 - The goal is to rank companies based on the number of products containing carcinogens.

Here we will also analyze the carginogenic chemical distribution across product categories and companies...
 - Certain product categories might contain a higher amount of carcinogenic ingredients, identifying trends in product formulations across different areas of the cosmetic industry.
   
Analyze chemical ingredient counts overtime...
 - Showing the ingredient counts overtime will show whether companies have been increasing/decreasing their use of carcinogenic ingredients in their formulations to attract consumers.
 - We can observe trends in initial reporting dates and chemical dislosure counts over time. 

Importance: 
- Public Health: Identifies areas for improved safety regulations and transparency.
- Economic Impact: Helps consumers make informed purchasing decisions, affecting company sales and trust. 
- Cultural Relevance: Protects groups relying heavily on cosmetics in daily life or traditions. Protects groups that need to use these products everyday for work.
  
# Analysis Question #2:
Which companies have the most products reported with discontinued chemicals?
- This will help identify companies that may be trying to limit certain ingredients from their forumulas or have products that contain chemicals no longer available.
- Capture the products and chemicals that are associated with these discontinued ingredients.
  
Here we can analyze product and chemical discontinuations overtime, what is the correlation between product and chemical discontinuation?
- Track the trend of product and chemical discontinuations overtime to see if there is a an increase or decrease in the use chemicals that have been discontinued.
- This can show if certain years saw a significant discontinuations of chemicals, possibly due to regulatory changes or pressure from consumers in the marketplace.
- We can observe the relationship between when products were discontinued and when the chemicals in those products were discontinued.
- Do products tend to be discontinued after the chemicals are phased out?

Importance:
- Public Health and Safety: Identifies companies historically linked to products containing harmful chemicals, even if they are now discontinued. This can inform ongoing regulatory scrutiny and public awareness.
- Regulatory Compliance: Demonstrates whether companies are actively addressing safety concerns and adapting to regulations.
- Consumer Trust: Highlights accountability and the extent to which companies are committed to improving product safety, influencing customer perceptions and loyalty.
- Economic Impact: Companies with numerous discontinued chemicals might face reputational risks, affecting market value and sales.

# Database Manipulations:
Overall Manipulation Details:
1. Filtering by Carcinogenic Ingredient Rating (at least 1A):
- Purpose: Focusing on chemicals with high carcinogenic potential and eliminate less important results from the data.
- Implementation: A filter was added to include only products with carcinogenic ingredients meeting the 1A minimum.
2. Grouping Data by Product Categories and Companies:
- Purpose: Analyze the distribution of carcinogenic ingredients across product categories. This will help to identify companies with the highest counts.
- Implementation: Group by "Primary Category". This groups products into categories like Hair Care, Personal Care, and Skin Care, for example. To count the number of products and ingredients calculations were done to count the number of carcinogenic chemicals and the amount of times they are included in each category or company.
3. Chemical Count Measure:
- Purpose: Determine how many unique carcinogenic chemicals are present in each product or associated with each company.
- Implementation: A distinct count calculation was used to the "Chemical Name" field for each company or category grouping.
4. Dates and Trends:
- Purpose: Track reporting trends and chemical disclosures over time.
- Implementation: Convert the "Initial Date Reported" field to a month-year format. Combine the distinct chemical counts by reporting month to visualize trends.

Analysis Question #1 Graphs:
1. Bubble Chart (Distribution of Carginogemic Ingredients Across Product Categories)
- Circle size represents the count of carcinogenic ingredients within each product category.
- Color coding to separate specific carcinogens by Chemical Name.
- A filter was included to separate by company if desired. Filters for Company Name allow us to focus on specific subsets of the data.
2. Bar Chart (Top Companies by Number of Products Containing Carginogenic Ingredients)
- A condition to filter companies with at least three brands meeting the carcinogenic threshold was applied.
- We used a stacked bar design to better display the counts for specific chemicals within companies.
- A filter was added to only include 5 Chemical Names (Benzene, Estragole, Ethylene Glycol, Ethylene Oxide, Formaldehyde, Methanol, o-Phenylphenol, and Phenacetin). Filters for Chemical Name allow us to focus on specific subsets of the data.
- A color code was added for these 5 chemicals listed above.
3. Line Graph (Chemical Count Reporting Overtime)
- Distinct counts of Chemical Ids plotted over time for each category to observe trends.
- Filter was added to separate out certain Primary Categories if desired.
- Color code was added by Primary Category.
- Initial Date Reported was converted to Month format on the x-axis of the graph.

Analysis Question #2 Graphs:
1. Bar Graph (Discontinued Count by Company)
- Focused analysis on a specific time frame (2001–2020) to avoid unnecessary outliers like the "Null" category by using a a date filter.
- Added filters in Tableau for Company Name.
- Sort Company Name by descending order, listing companies with the most chemicals counted at the top and least chemical count at the bottom.
- Add color code to Company Name to make graph communicative and easy to read.
2. Line Graph (Trends in Product Discontinuations Overtime by Subcategory)
-  Convert dates into Years to accurately compare discontinuation dates and simply the visualization.
-  Grouped data by "Company Name" field in Tableau.
-  Grouped data by "Subcategory" field in Tableau.
-  Apply a filter to Subcategory to only inlude 5 subcategories at random (Blushes, Eye Shadow, Face Powders, Hair Dyes and Colors, and Skin Cleansers).
-  Add a color code to subcategories for the 5 subcategories listed above.
3. Line Graph (Chemicals Banned by Date)
- To eliminate the null values in the dataset, which indicate missing discontinuation dates, apply a filter by Year and deselect "Null" as a Year.
- Convert dates into Years consistently.
- Used Tableau's COUNT() function to calculate the total number of Chemical Ids discontinued each year to show the impact of these chemical bans.


# Analysis and Results: 
Analysis Question #1: Which companies have the highest number of products containing carcinogenic ingredients with a rating of at least 1A? Analyze distribution across product categories and companies. 

What did we find?
- Elizabeth Arden, Inc. and A.P. Deauville, LLC are among the top companies with the highest number of products containing carcinogenic ingredients, shown by the bar graph, which highlights their significantly higher counts of carcinogenic chemicals compared to other companies. 
- The bubble chart illustrates that product categories such as fragrances, skin care products, hair coloring products, and bath products have the highest occurrence of carcinogenic ingredients. It is likely that companies like Elizabeth Arden and A.P. Deauville have their products distributed across these prominent categories.
- Notably, fragrances appear to be particularly problematic, often containing multiple chemicals such as benzene and formaldehyde. In addition, hair coloring and bath products are notable contributors, indicating that companies with a high product count may specialize in these areas.

![Screenshot 2024-11-23 150352](https://github.com/user-attachments/assets/e3b31b69-4807-4380-bb13-8872900e8542)

![Screenshot 2024-11-23 150415](https://github.com/user-attachments/assets/8ba835a1-c920-4256-8893-b042c629e1ed)


Analysis Question #1: Analyze chemical ingredient counts overtime. 
What did we find?
- The line graph shows trends in reporting dates and chemical disclosure counts over time, separated by category. Peaks in chemical counts in the fall season months, especially for the “Makeup Products” category, correlate to an increased use of these carcinogenic ingredients. The correlation between categories may represent changes in chemical regulatory reporting and events like product launches or seasonal innovation.
- For example, fall months could align with the coming of new regulations requiring companies to disclose additional chemical information, especially for carcinogenic ingredients. Many regulatory agencies set reporting deadlines that coincide with the end of fiscal quarters or calendar quarters. September often marks the end of Q3, potentially urging companies to disclose new chemical ingredients.
- Additionally, spikes of chemical counts during the fall may be largely due to seasonal promotion. Fall is a common time for companies to launch new products for the holiday season, leading to increased reporting as part of the regulatory process for new product approval or chemical ingredient disclosure.

![Screenshot 2024-11-23 150438](https://github.com/user-attachments/assets/79ca2699-4ed4-44af-b5eb-cbc383ef95f3)


Analysis Question #2: Which companies have the most products reported with discontinued chemicals?

What did we find?
- The data reveals that The Procter & Gamble Co. stands out as the company with the most products reported containing discontinued chemicals, with nearly 2,800 instances, far surpassing other companies. 
- Following Procter & Gamble, Victoria’s Secret Beauty and Elizabeth Arden, Inc. have over 1,000 discontinued chemical reports each, while companies like MAESA LLC, Bath & Body Works, and The Boots Company PLC also report significant counts, ranging between 600 and 1,000. Smaller contributors, such as Yves Rocher Inc., Too Faced Cosmetics, and Nars Cosmetics, have fewer than 500 counts each.
- Over time, the trend shows a peak in discontinued chemicals between 2013 and 2015, with 2013 being the year with nearly 2,000 reported bans. However, this number declined sharply by 2020, indicating a potential reduction in regulatory actions or improved compliance within the industry. 
- The significant lead by Procter & Gamble may reflect either heightened regulatory scrutiny or their broader product portfolio, leading to more chemical reports compared to other companies.

![Screenshot 2024-11-23 150529](https://github.com/user-attachments/assets/38c2a68f-b45d-43bb-95cd-5e905f2fe0f8)

![Screenshot 2024-11-23 150625](https://github.com/user-attachments/assets/936f8d82-0405-4923-9998-204215991133)


Analysis Question #2: After analyzing product and chemical discontinuations overtime, what is the correlation between product and chemical discontinuation?

![Screenshot 2024-11-23 150602](https://github.com/user-attachments/assets/1fa6f87f-d899-402d-9866-e62562bfe47e)

What did we find?
- Here, CDPHId is used as a unique product identifier to count distinct discontinued products over many years. The line graph "Trends in Product Discontinuations Overtime by Subcategory" illustrates the distinct count of products discontinued over time, separated by color by subcategories. 
- Peaks in certain years highlight potential regulatory impacts, market shifts, or changes in consumer demand. 
- As a result of the chemical bans, product discontinuations are present. There is a correlation between the years where more chemicals are banned and increased product discontinuations.
- For example, subcategories on the "Trends in Product Discontinuations Overtime by Subcategory" line graph experiencing significant discontinuation spikes, like "Hair Dyes and Colors", might rely on chemicals that became banned during this timeframe, aligning with the increase in 2016 on the "Chemicals Banned by Date" line graph timeline. Similarly in 2013, we see a noticeable spike to the “Eyeshadow” subcategory, correlating to the increase in 2013 on the "Chemicals Banned by Date" timeline.
- Overall trends suggest that peaks in chemical bans (2010–2016) align with periods of higher product discontinuation, suggesting regulatory or market shifts impacting both. Regulatory actions banning chemicals likely prompted companies to discontinue products that depended on these ingredients.


# Tableau Packaged Workbook:
