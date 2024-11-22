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
  
Here we can analyze product and chemical discontinuations overtime...
- Track the trend of product and chemical discontinuations overtime to see if there is a an increase or decrease in the use chemicals that have been discontinued.
- This can show if certain years saw a significant discontinuations of chemicals, possibly due to regulatory changes or pressure from consumers in the marketplace.
  
Analyze the correlation between product and chemical discontinuation...
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
3. Line Graph (Chemical Count Reporting Overtime Line Graph)
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
2. Line Graph (Trends in Product Discontinuations Overtime by Subcategory Line Graph)
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

# Tableau Packaged Workbook:
