

# World Economic Indicators

+ The dataset is sourced from the Maven Analytics platform: https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=World%20Economic%20Indicators
  
## Research Questions: 
1. Which countries have experienced the highest growth in population and GDP? Is there overlap?

2. Where regions saw the most growth in HDI in the 21st century?

3. Which factors are highly correlated with life expectancy?

4. Which factors differentiate "High Income" vs "Low Income" Countries?

## Tools used :

Power BI, Python 

> [!NOTE]
> In this analysis, I aim to explore and compare the effectiveness of Power BI and Python in handling and analyzing data. I will focus particularly on the World Economic Indicators dataset that requires imputation techniques, using descriptive statistics to address missing values. By applying methods such as mean and median imputation, I will assess how each tool manages data preprocessing and its impact on the accuracy and reliability of the analysis. 
This comparative study will provide insights into the strengths and limitations of Power BI and Python in dealing with incomplete data and performing robust statistical analyses.

## Dataset exploration 
+ The dataset contains 2 seperate Excel files :
  
**1. Human Development Index(HDI):**
   * **Column Num**: 1008,   **Row Num**: 206
     
     - **Iso 3** : The three letter code representing the country.
     - **Country**: The name of the country.
     - **hdicode**: refers to the HDI (Human Development Index) grouping code used by the United Nations Development Programme (UNDP) to categorize countries based on their HDI values. **Very High Human Development**, **High Human Development**, **Medium Human Development**, **Low Human Development**.
     - **Region**: refers to the geographic or economic groupings used by the United Nations Development Programme (UNDP) to categorize countries based on their development characteristics. Regions listed in the [Region column]: **Sub-Saharan Africa**, **East Asia and Pacific**, **Europe and Central Asia**, **Latin America and the Caribbean**, and **South Asia**. _**Middle East and North Africa** is missing._
     - **hdi_rank_2021**: represents the Human Development Index (HDI) rank for each country in the year 2021, with 1 being the highest rank  and 191 being the lowest.
     - **hdi_xxxx**: refers to the Human Development Index (HDI) of a country for the specific year xxxx. _HDI is a combined index that measures a country's average achievements in three basic aspects of human development: **health** (life expectancy at birth), **education** (mean years of schooling and expected years of schooling), and **standard of living** (gross national income per capita)._
     - **le_xxxx**: The country's longevity rate in year xxxx.
     - **eys_xxxx**: The country's predicted years of schooling.
     - **mys_xxxx**: The country's average years of education.
     - **gnipc_xxxx**: The gross national income per person in dollars.
     - **gdi_group_2021**: The per capita gross national income expressed in dollars.
     - **gdi_xxxx**: Gender Development Measure in Year XXXX.
     - **hdi_f_xxxx**: Female Human Development Index for Year XXXX.
     - **le_f_xxxx**: Female Life Expectancy at Birth for Year XXXX.
     - **eys_f_xxxx**:  Female Expected Years of Education in Year XXXX.
     - **mys_f_xxxx**: Female Mean Years of Education in Year XXXX.
     - **gni_pc_f_xxxx**:  Female Gross National Income per Capita for Year XXXX.
     - **hdi_m_xxxx**: Male Human Development Index for Year XXXX.
     - **le_m_xxxx**: Male Life Expectancy at Birth for Year XXXX.
     - **eys_m_xxxx**: Male Expected Years of Schooling for Year XXXX.
     - **mys_m_xxxx**: Average Years of Schooling for Males in XXXX.
     - **gni_pc_m_xxxx**: Male Gross National Income per Capita in Year XXXX.
     - **ihdi_xxxx**: Inequality-Adjusted Human Development Index for Year XXXX.
     - **coef_ineq_xxxx**: Human Inequality Coefficient for Year XXXX.
     - **loss_xxxx**: Percentage of Overall Loss in Year XXXX.
     - **ineq_le_xxxx**:Inequality in Life Expectancy for Year XXXX.
     - **ineq_edu_xxxx**: Inequality in Education for Year XXXX. 
     - **ineq_inc_xxxx**: Income Inequality for Year XXXX. 
     - **gii_rank_2021**: Gender Inequality Index Ranking for 2021. 
     - **gii_xxxx**: Gender Inequality Index for Year xxxx. 
     - **mmr_xxxx**: Maternal Mortality Rate for Year xxxx. 
     - **abr_xxxx**: Adolescent Birth Rate (per 1,000 women aged 15-19) for Year xxxx. 
     - **se_f_xxxx**: Female Population with Secondary Education (25+ years) in Year xxxx.
     - **se_m_xxxx**: Male Population with Secondary Education (25+ years) in Year xxxx. 
     - **pr_f_xxxx**: Share of Women in Parliament (% Seats) for Year xxxx. 
     - **pr_m_xxxx**: Share of Men in Parliament (% Seats) for Year xxxx. 
     - **lfpr_f_xxxx**: Female Labour Force Participation Rate (% ages 15 and older) in Year xxxx. 
     - **lfpr_m_xxxx**: Male Labour Force Participation Rate (% ages 15 and older) in Year xxxx. 
     - **rankdiff_hdi_phdi_2021**: Difference in HDI Ranking Compared to 2020. 
     - **phdi_xxxx**: HDI Adjusted for Planetary Pressures (value) in Year xxxx.
     - **diff_hdi_phdi_xxxx**: Difference (%) between HDI and Planetary Pressures-Adjusted HDI in Year xxxx. 
     - **co2_prod_xxxx**: Carbon Dioxide Emissions per Capita (Production) in Year xxxx (tonnes). 
     - **mf_xxxx**: Material Footprint per Capita in Year xxxx (tonnes). 

     
**2. Development Indicators:**
   + **Column Num**: 15,  **Row Num**: 4009

     - **Country Name**
     - **Country code**: is a three-letter abbreviation that uniquely identifies a country. 
     - **Region**: refers to the specific geographic or economic grouping assigned to a country by the World Bank. (**Sub-Saharan Africa**, **East Asia and Pacific**, **Europe and Central Asia**, **Latin America and the Caribbean**, **Middle East and North Africa**, and **South Asia**.)
     - **Income Group**: refers to the classification assigned by the World Bank that categorizes countries based on their gross national income (GNI) per capita. **Low Income** (GNI per capita of $1,085 or less), **Lower-Middle Income** (GNI per capita between $1,086 and $4,255), **Upper-Middle Income** (GNI per capita between $4,256 and $13,205), **High Income** (GNI per capita of $13,206 or more).
     - **Year**: The Year in which the statistics were recorded.
     - **Birth rate, crude (per 1,000 people)**: measures the number of live births per 1,000 individuals in the population within a year, without adjusting for age or sex distribution.
     - **Death rate, crude (per 1,000 people)**: measures the number of deaths per 1,000 individuals in the population within a year, without adjusting for age or sex distribution.
     - **Electric power consumption (kWh per capita)**: measures the average amount of electrical energy consumed per person in a country over the course of a year, expressed in kilowatt-hours.
     - **GDP (USD)**: refers to the total market value of all goods and services produced within a country in a year, expressed in US dollars.
     - **GDP per capita (USD)**: measures the average economic output per person in a country, calculated by dividing the total Gross Domestic Product (GDP) by the population, and expressed in US dollars.
     - **Individuals using the Internet (% of population)**:  refers to the percentage of people in a country who have accessed the internet in a given year.
     - **Infant mortality rate (per 1,000 live births)**: measures the number of infants who die before reaching one year of age per 1,000 live births in a given year.
     - **Life expectancy at birth (years)**: is the average number of years a newborn is expected to live if current mortality rates at the time of birth remain constant throughout their life.
     - **Population density (people per sq. km of land area)**:  measures the number of people living per square kilometer of land area in a country.
     - **Unemployment (% of total labor force) (modeled ILO estimate)**:  represents the percentage of the labor force that is unemployed but actively seeking work, as estimated by the International Labour Organization (ILO).

# HDI table

## Exploratory Data Analysis 

**1.** **Erros & Data Completness**:
   + There were no errors.
   + There were Blanks and Nulls:
     * Blanks were found in the [hdicode] & [region]:

  ![image](https://github.com/user-attachments/assets/7e0ae7de-2f7e-49ef-8733-2a886d6fd424)

  * Nulls were found in:
      1. **HDI** year columns ranging from 2% - 10%.
    
      2. **EYS** year columns only 2% and only between the years 2000 - 2006.
          
      4. **MYS** year columns only 2% and only between the years 2000 - 2009.
          
      6. **GNI_PC_F** year columns only 4% for all years.
          
      7. **GNI_PC_M** year columns only 4% for all years.
          
      8. **GII** year columns ranging from 8% - 25% for all years.
           
      9. **IFPR_F** year columns only 4% for all years.
           
      10. **IFPR_M** year columns only 4% for all years.

 **2.** **Data Consistency**:
     
  * **The [ISO 3]**: a column that is expected to contain the three-letter codes for countries as defined by the ISO 3166-1 standard. However, in the current column there included the HDI Groupings and Regional Groupings as well.
    
       ![image](https://github.com/user-attachments/assets/c0b27f45-4aa3-4402-9df9-46eba1deadf1)

* **HDI Groupings**: ZZA.VHHD: Very High Human Development | ZZB.HHD: High Human Development | ZZC.MHD: Medium Human Development | ZZD.LHD: Low Human Development

* **Regional Groupings**: ZZE.AS: Asia | ZZF.EAP: East Asia and Pacific | ZZG.ECA: Europe and Central Asia | ZZH.LAC: Latin America and Caribbean | ZZI.SA: South Asia | ZZJ.SSA: Sub-Saharan Africa | ZZK.WORLD: World Aggregate

> [!WARNING]
>* **The [region]**: The region **Middle East & North Africa (MENA)** was missing from the dataset. And countries that normally belong to MENA were incorrectly assigned to other regions.

  For example:
  
  A. Algeria: Initially assigned to "Asia" instead of "Middle East & North Africa (MENA).
       
  B. Israel: Initially assigned to "Europe and Central Asia" instead of "Middle East & North Africa (MENA).
       
  C. Egypt: Initially assigned to "Asia" instead of "Middle East & North Africa (MENA)
       
 ## Cleaning Process with Power BI and Python 

***
  > [!IMPORTANT]
 > * The analysis is focused on the **21st century**. Any non related column was removed.
***

  📊 **Power Query**: The process is very straightforward—simply uncheck the columns using the _Choose Columns_ functionality.

  ![image](https://github.com/user-attachments/assets/5dbcc8f0-3e53-411f-8cbb-261cda410785)

  🐍 **Pandas**:  The process is also simple by creating a list of columns to keep. 

  ```ruby
  columns_to_keep = [
    'iso3', 'country', 'hdicode', 'region', 'hdi_rank_2021',
    'hdi_2000', 'hdi_2001', 'hdi_2002', 'hdi_2003', 'hdi_2004', 'hdi_2005', 'hdi_2006', 'hdi_2007',
    'hdi_2008', 'hdi_2009', 'hdi_2010', 'hdi_2011', 'hdi_2012', 'hdi_2013', 'hdi_2014', 'hdi_2015',
    'hdi_2016', 'hdi_2017', 'hdi_2018', 'hdi_2019', 'hdi_2020', 'hdi_2021',
    'le_2000','le_2001', 'le_2002', 'le_2003', 'le_2004', 'le_2005', 'le_2006', 'le_2007', 'le_2008', 
    'le_2009', 'le_2010', 'le_2011', 'le_2012', 'le_2013', 'le_2014', 'le_2015', 'le_2016', 'le_2017',
    'le_2018', 'le_2019', 'le_2020', 'le_2021',
    'eys_2000', 'eys_2001', 'eys_2002', 'eys_2003', 'eys_2004', 'eys_2005', 'eys_2006', 'eys_2007',
    'eys_2008', 'eys_2009', 'eys_2010', 'eys_2011', 'eys_2012', 'eys_2013', 'eys_2014', 'eys_2015',
    'eys_2016', 'eys_2017', 'eys_2018', 'eys_2019', 'eys_2020', 'eys_2021',
    'mys_2000', 'mys_2001', 'mys_2002', 'mys_2003', 'mys_2004', 'mys_2005', 'mys_2006', 'mys_2007',
    'mys_2008', 'mys_2009', 'mys_2010', 'mys_2011', 'mys_2012', 'mys_2013', 'mys_2014', 'mys_2015',
    'mys_2016', 'mys_2017', 'mys_2018', 'mys_2019', 'mys_2020', 'mys_2021',
    'gnipc_2000', 'gnipc_2001', 'gnipc_2002', 'gnipc_2003', 'gnipc_2004', 'gnipc_2005', 'gnipc_2006',
    'gnipc_2007', 'gnipc_2008', 'gnipc_2009', 'gnipc_2010', 'gnipc_2011', 'gnipc_2012', 'gnipc_2013',
    'gnipc_2014', 'gnipc_2015', 'gnipc_2016', 'gnipc_2017', 'gnipc_2018', 'gnipc_2019', 'gnipc_2020',
    'gnipc_2021',
    'gni_pc_f_2000', 'gni_pc_f_2001', 'gni_pc_f_2002', 'gni_pc_f_2003', 'gni_pc_f_2004', 
    'gni_pc_f_2005', 'gni_pc_f_2006',
    'gni_pc_f_2007', 'gni_pc_f_2008', 'gni_pc_f_2009', 'gni_pc_f_2010', 'gni_pc_f_2011',
    'gni_pc_f_2012', 'gni_pc_f_2013', 'gni_pc_f_2014', 'gni_pc_f_2015', 'gni_pc_f_2016',
    'gni_pc_f_2017', 'gni_pc_f_2018', 'gni_pc_f_2019', 'gni_pc_f_2020', 'gni_pc_f_2021',
    'gni_pc_m_2000', 'gni_pc_m_2001', 'gni_pc_m_2002', 'gni_pc_m_2003',
    'gni_pc_m_2004', 'gni_pc_m_2005', 'gni_pc_m_2006', 'gni_pc_m_2007', 'gni_pc_m_2008',
    'gni_pc_m_2009', 'gni_pc_m_2010', 'gni_pc_m_2011', 'gni_pc_m_2012', 'gni_pc_m_2013',
    'gni_pc_m_2014', 'gni_pc_m_2015', 'gni_pc_m_2016', 'gni_pc_m_2017', 'gni_pc_m_2018',
    'gni_pc_m_2019', 'gni_pc_m_2020', 'gni_pc_m_2021',
    'gii_2000', 'gii_2001', 'gii_2002',
    'gii_2003', 'gii_2004', 'gii_2005', 'gii_2006', 'gii_2007', 'gii_2008', 'gii_2009', 'gii_2010',
    'gii_2011', 'gii_2012', 'gii_2013', 'gii_2014', 'gii_2015', 'gii_2016', 'gii_2017', 'gii_2018',
    'gii_2019', 'gii_2020', 'gii_2021', 
    'lfpr_f_2000', 'lfpr_f_2001', 'lfpr_f_2002', 'lfpr_f_2003',
    'lfpr_f_2004', 'lfpr_f_2005', 'lfpr_f_2006', 'lfpr_f_2007', 'lfpr_f_2008', 'lfpr_f_2009',
    'lfpr_f_2010', 'lfpr_f_2011', 'lfpr_f_2012', 'lfpr_f_2013', 'lfpr_f_2014', 'lfpr_f_2015', 
    'lfpr_f_2016', 'lfpr_f_2017', 'lfpr_f_2018', 'lfpr_f_2019', 'lfpr_f_2020', 'lfpr_f_2021', 
    'lfpr_m_2000', 'lfpr_m_2001',
    'lfpr_m_2002', 'lfpr_m_2003', 'lfpr_m_2004', 'lfpr_m_2005', 'lfpr_m_2006', 'lfpr_m_2007',
    'lfpr_m_2008', 'lfpr_m_2009', 'lfpr_m_2010', 'lfpr_m_2011', 'lfpr_m_2012', 'lfpr_m_2013',
    'lfpr_m_2014', 'lfpr_m_2015', 'lfpr_m_2016', 'lfpr_m_2017', 'lfpr_m_2018', 'lfpr_m_2019', 
    'lfpr_m_2020', 'lfpr_m_2021'
]

# Drop columns not in the list of columns to keep
df = df[columns_to_keep]

df.head()
```
   
***
   * The **[ISO 3]**: contained the HDI Groupings and Regional Groupings. I filtered out the corresponding rows from the [ISO 3].
***

   📊 **Power Query**: Straightforward process by unselecting the rows to be filtered out. 

   🐍 **Pandas**: Simple and efficient with a few lines of code.

 ```ruby
  rows_to_filter_out = [
    'ZZA.VHHD', 'ZZB.HHD', 'ZZC.MHD', 'ZZD.LHD', 'ZZE.AS',
    'ZZF.EAP', 'ZZG.ECA', 'ZZH.LAC', 'ZZI.SA', 'ZZJ.SSA'
]

df = df[~df['iso3'].isin(rows_to_filter_out)]

df['iso3'].tail(10)
```

***
   * The **[country]**: The column contained the full names of regional groupings, which were filtered out. Additionally, some country names were simplified for consistency and ease of use. For example, "Iran, Islamic Rep" was renamed to "Iran" to standardize names and ensure uniformity across the dataset.
***

   📊 **Power Query**: Simplification of country names was an easy process using the _replace_ functionality. 

   🐍 **Pandas**: The process involves creating _a dictionary with original and simplified names_, then using the _replace_ method. 

```ruby
country_rename = {
    "Iran, Islamic Rep": "Iran",
    "United States of America": "USA",
    "United Kingdom": "UK",
    "Russian Federation": "Russia",
    "Venezuela, Bolivarian Republic of": "Venezuela",
    "Bolivia (Plurinational State of)": "Bolivia",
    "Congo (Democratic Republic of the)": "Congo, Dem. Rep.",
    "Congo": "Congo, Rep.",
    "Eswatini (Kingdom of)": "Eswatini",
    "Hong Kong, China (SAR)": "Hong Kong",
    "Korea (Democratic People's Rep. of)" : "North Korea",
    "Korea (Republic of)": "South Korea",
    "Micronesia (Federated States of)": "Micronesia",
    "Moldova (Republic of)": "Moldova",
    "Palestine, State of": "Palestine",
    "Syrian Arab Republic": "Syria",
    "Tanzania (United Republic of)": "Tanzania",
    "Venezuela (Bolivarian Republic of)" : "Venezuela",
    "Viet Nam": "Vietnam",
    "Lao People's Democratic Republic": "Laos",
    "Iran (Islamic Republic of)": "Iran"
    
}

df.loc[:, 'country'] = df['country'].replace(country_rename)
print(df['country'])
```

***
   * The **[hdicode]** column contained a total of 15 blank rows. To maintain consistency, I replaced the blanks with Null, and then with N/A. In addition, I replaced the more general categories: Low, Medium, High, Very High with the more informative codes as found earlier in the [ISO 3] (VHHD, HHD, MHD, LHD). 
***
   ![image](https://github.com/user-attachments/assets/5e685cdc-f8bc-4695-b425-e3f505a5da37)


 📊 **Power Query**: The process of handling NaN and replacing categories is straightforward with user-friendly interfaces for _replacing_ values and handling nulls. 

 🐍 **Pandas**: While more code is required, Pandas offers flexibility and powerful functions like _fillna_ and _replace_ to efficiently handle such data transformations programmatically

```ruby
df.loc[:, 'hdicode'] = df['hdicode'].fillna('N/A')

category_replacing = {
    'Low': 'LHD',
    'Medium': 'MHD',
    'High': 'HHD',
    'Very High': 'VHHD'
}

df.loc[:, 'hdicode'] = df['hdicode'].replace(category_replacing)
```

***
   * The **[region]** column contained 55 blank rows. However, instead of filling the blanks with N/A, I found it easier to identify the correct region for each country. Therefore, I **filled the blanks with the appropriate region.**
***

   📊 **Implementation with Power Query**:

   **1.** I first created a new conditional column called [Region_filled], listing only the countries whose region was missing from the original [region] column:
      
  ![image](https://github.com/user-attachments/assets/af53f8e4-4781-406e-92c6-c24ce333ad1d)

   **2.**  Then I used this conditional column to fill the blanks of the original region column: 

 ![image](https://github.com/user-attachments/assets/ba444660-76b9-4b1c-95d7-b42d6d795e3a)

   **3.**  The [Region_NO Blanks] column has been updated, and the previously blank entries are now filled with the corresponding region names. 

   ![image](https://github.com/user-attachments/assets/ed0833aa-6a0f-4249-9fee-ff795750c4f4)

   🐍 **Implementation with Pandas**:

```ruby
## Filling the blanks with the appropriate region

region_correct = {
    'Andorra': 'ECA', 'Australia': 'EAP', 'Austria': 'ECA', 'Belgium': 'ECA', 'Bulgaria': 'ECA',
    'Canada': 'NA', 'Switzerland': 'ECA', 'Cyprus': 'ECA', 'Czechia': 'ECA', 'Germany': 'ECA',
    'Denmark': 'ECA', 'Spain': 'ECA', 'Estonia': 'ECA', 'Finland': 'ECA', 'France': 'ECA',
    'UK': 'ECA', 'Greece': 'ECA', 'Hong Kong': 'EAP', 'Croatia': 'ECA', 'Hungary': 'ECA',
    'Ireland': 'ECA', 'Iceland': 'ECA', 'Israel': 'MENA', 'Italy': 'ECA', 'Japan': 'EAP',
    'South Korea': 'EAP', 'Liechtenstein': 'ECA', 'Lithuania': 'ECA', 'Luxembourg': 'ECA',
    'Latvia': 'ECA', 'Monaco': 'ECA', 'Netherlands': 'ECA', 'Norway': 'ECA', 'New Zealand': 'EAP',
    'Portugal': 'ECA', 'Romania': 'ECA', 'Russia': 'ECA', 'San Marino': 'ECA', 'Slovakia': 'ECA',
    'Slovenia': 'ECA', 'Sweden': 'ECA', 'United States': 'NA', 'Malta': 'ECA', 'Poland': 'ECA', 'World': 'World'
}

df.loc[df['region'].isna(), 'region'] = df.loc[df['region'].isna(), 'country'].map(region_correct)
```

***
   **4.** The next challenge with the updated [Region_NO Blanks] is the incorrect assignment of certain countries to wrong regions and the absence of the **Middle East & North Africa (MENA)** region.
***

   📊 **Implementation with Power Query**:  

  - To address the issue of incorrect regional assignments for some countries, I created a new query with the correct region information, merged this with the main dataset, expanded the merged column to include the correct regions, and used a conditional formula to update the regions based on the mapping table.

![image](https://github.com/user-attachments/assets/e192124f-4beb-4a81-bc62-ac837eab459d)                 ![image](https://github.com/user-attachments/assets/456506b2-ab12-4814-b634-d1c5234abdea)

**5.** To avoid redundancy, I removed the original [region] and the [Region Filled] column, [Region_NO Blanks], and Country Region Mapping.Region. I kept the [Updated Region] and rename it back to [region]. 

 * **Conclusion**: both the [hdicode] and [region] columns comply with the rules of consistency and readability.

  ![image](https://github.com/user-attachments/assets/75f2c276-a113-4050-8b1a-0c31c2fcd69a)
  
 🐍 **Implementation with Pandas**: Used list-based assignment to identify MENA countries and directly updated the region column. And Used a dictionary-based mapping to update incorrect regions.

```ruby
## Working with [region] and assigning the region MENA to the appropriate countries. 

mena = [
    'Algeria', 'Bahrain', 'Djibouti', 'Egypt', 'Iran', 'Iraq', 'Israel', 'Jordan',
    'Kuwait', 'Lebanon', 'Libya', 'Morocco', 'Oman', 'Qatar', 'Saudi Arabia', 
    'Syria', 'Tunisia', 'United Arab Emirates', 'Yemen'
]

df.loc[df['country'].isin(mena), 'region'] = 'MENA'

```


   ## Addressing the null values

   ### 📊 Implementation with Power Query:
    
   #### A. HDI xxxx Fields 

   Initially, I considered using the mode, but due to multiple values sharing the highest frequency in some HDI fields, a clear mode could not be determined. As an alternative, I opted to use either the average or the median as an imputation method. However, the mean is sensitive to outliers. Because, outliers can pull the mean towards them, making it less representative of the central tendency of the data. So, to proceed cautiously, I first had to check for outliers. But the distribution of the data will define first the method to use in order to detect outliers.

   * **If data follows Normal Distribution**: Z-score for detecting outliers.

   * **If data follows Non - Normal Distribution**: better to use methods that do not assume normality, such as the interquartile range (IQR) method or the percentile method.

   Approach followed for checking of distribution:

1.  **Plotted Histograms.**  
  
      ![image](https://github.com/user-attachments/assets/7b071cd6-0d9e-46a0-8be1-7c9ae824744c)

- **Left-Skewed Nature**: All distributions are left-skewed, meaning that the majority of the data points (countries) have higher HDI values. However, a significant number of countries with lower HDI values (closer to 0.2-0.4) create a long tail to the left.
- **Mean vs. Median**: 1. The mean being lower than the median further confirms the left-skewed nature of the data.
                       2. Both the mean and median have increased over the years, indicating an overall improvement in HDI scores for the countries.
                       3. The gap between the mean and median shows a slight decrease by 2020, suggesting that the distribution is becoming more symmetrical *. 
- **Consistency Over Years**: The general pattern remains consistent over the years, with slight improvements in HDI values (increasing mean and median).
- **Central Tendency Interpretation**: In left-skewed distributions, the median is typically a more accurate measure of central tendency than the mean because it is less affected by the long tail of lower values.
- **Outlier Detection method**: Skewness influences the choice of outlier detection methods. The Interquartile Range (IQR) method is preferred since it does not assume normality and effectively identifies outliers in skewed distributions.


  **2.** **Outlier Detenction with IQR**

> [!TIP]
> *For better organization:*
> *I created subfolders to organize the measures I needed: one for building histograms to check data distribution and another for calculating the IQR to check for outliers.*

  ![image](https://github.com/user-attachments/assets/e5e50ce4-d9c9-4507-97fc-74b4860dd1a2)



  **A**. **I created the measures needed to calculate the IQR using the following formula:** 

  ![image](https://github.com/user-attachments/assets/0e1de08e-9922-4e19-bd1f-40859ca99faf)

  *The image is sourced: https://janiceto.github.io/ml-knowledge-base/01-intro/stats-basics/boxplot.html*

  Here is a multi-card display that includes Q1, Q3, the IQR, as well as the maximum and minimum values for each of the years: 2000, 2005, 2010, 2015, and 2020.

  ![image](https://github.com/user-attachments/assets/4491936e-d92b-4ccd-8aef-ad6170495a62)

  Then, I combined all the above measures to construct the IQR formula

  ![image](https://github.com/user-attachments/assets/2e3f21f6-7878-4b9e-b216-adfe748aed42)

> [!NOTE]
> **There were found NO OUTLIERS!**
  
  

  ![image](https://github.com/user-attachments/assets/fbfa6d3a-0e0c-42b0-b09a-3ec9458c1610)

  The absence of outliers with the IQR method in a left-skewed dataset might suggest that the data has broad or mild skewness without extreme values.

  However, it’s important to verify the data spread and consider additional methods. That’s why, I plotted the data in scatterplots.

  ![image](https://github.com/user-attachments/assets/38d02074-1f1c-4169-b691-97afca086d03)

  **C**. **Previous result verification:** 
  
  * Overall, the data in these scatter plots do not exhibit significant outliers, as all points generally adhere to the expected linear trend.

  1. **hdi_2000**: The points form a tight linear cluster without any noticeable deviations. There are no clear outliers.
  2. **hdi_2005**: Similarly, the points are closely clustered along the diagonal, indicating no apparent outliers.
  3. **hdi_2010**: This plot shows a similar pattern, with one point slightly deviating from the line but still close enough to not be considered a significant outlier.
  4. **hdi_2015**: The points are tightly clustered, and there are no significant deviations from the linear trend.
  5. **hdi_2020**: Again, the points follow a linear pattern closely, with no clear outliers.


  **Conclusion:** The absence of outliers identified by the IQR method, combined with the visual inspection that shows no significant deviations, leads me to conclude that there are no outliers in my data. 

 > [!IMPORTANT]
 > **Imputation Method:** Typically, when outliers are present, we use the median to impute nulls, and when there are no outliers, we use the mean. Here we do not have outliers but the data is left-skewed. The **median** is likely a more appropriate measure of central tendency for imputing the nulls, as it is less affected by skewness compared to the mean.


   #### B. Rest Fields 
   
  *For the remaining columns with null values, I will plot histograms to check the distributions but will not perform outlier detection as extensively as for the HDI column. This decision is based on the project's focus on practice and skill development, and to save time. In the case of the HDI column, outlier analysis revealed only left skewness without significant outliers, making a similar in-depth analysis for the remaining columns less critical. In addition, similar to the analysis performed for the HDI columns, the distribution analysis was also conducted for selected years.*
  
  **1. Addressing the null values in the [EYS] fields.**

  ![image](https://github.com/user-attachments/assets/018fd4a3-2843-4506-a929-923162f5605c)

  *Null values were present only in the years between 2000 and 2006.*
    
  - **Nearly symmetrical Nature**: The close proximity of mean and median values across the years suggests that there is no significant skew.
    
  > [!IMPORTANT]
  > - **Imputation Method:** The nearly symmetrical distribution supports the use of the **mean** for imputation. The consistency in the proximity of mean and median values over time indicates that the data has maintained a stable central tendency, making the mean a reliable measure for handling missing values.


  **2. Addressing the null values in the [MYS] fields.**

![image](https://github.com/user-attachments/assets/fb404774-2313-46f7-8fed-14bf5d2607e9)

*Null values were present only in the years between 2000 and 2009.*

  - **Left-Skewed Nature for MYS 2000:** The mean is significantly lower than the median indicating a left-skewed distribution with a longer tail towards lower values.

  - **Nearly Symmetrical Nature for MYS 2009:** The mean is close to the median, suggesting a nearly symmetrical distribution with slight left skew.

  > [!IMPORTANT]
  > - **Imputation Method:** Although the histogram for MYS 2009 shows a nearly symmetrical distribution, I will use the **median** for imputation because of the clear left skew in 2000. This ensures a consistent and robust approach across all MYS years columns.


**3. Addressing the null values in the [GNI_PC_F] fields.**

![image](https://github.com/user-attachments/assets/d59af4c6-1f27-459c-b37f-838be13ec3e6)

*Null values were observed in the data for all years.*

- **Right-Skewed Nature for Female GNI per Capita 2000:** The mean is significantly higher than the median, indicating a right-skewed distribution with a longer tail towards higher values.

- **Right-Skewed Nature for Female GNI per Capita 2010:** The distribution remains right-skewed, though the skewness is less pronounced compared to 2000, with the mean still higher than the median.

- **Right-Skewed Nature for Female GNI per Capita 2020:** The mean is still higher than the median, reflecting a right-skewed distribution, and the distribution extends to even higher values up to 70K.

> [!IMPORTANT]
> - **Imputation Method:** Given the right skewness observed across all selected years, using the **median** for imputation is a suitable choice. The median is less influenced by high-value outliers, providing a more robust central tendency measure for handling missing values.


**4. Addressing the null values in the [GNI_PC_M] fields.**

![image](https://github.com/user-attachments/assets/046e57c5-fa3c-45d8-a906-51567f10ba1d)

*Null values were observed in the data for all years.*

- **Right- skewed distributions**: Across all selected years, the distributions of GNI per Capita demonstrate a right-skewed nature, with most countries having relatively low GNI per Capita values.
- This consistent right skewness suggests that the **majority of countries fall below the mean** GNI per Capita, with only a few outliers having significantly higher values.
  
> [!IMPORTANT]
> - **Imputation Method:** Given the observed right-skewed distributions, using the **median** for imputation is a suitable choice.


**5. Addressing the null values in the [GII] fields.**

![image](https://github.com/user-attachments/assets/f692dafd-1c09-49af-b8c9-83bb29748d49)

*Null values were observed in the data for all years.*

- **Symmetrical Distribution for GII 2000:** The mean is nearly equal to the median, indicating a balanced spread of GII values.

- **Left-Skewed Nature for GII 2005, 2015, and 2020:** The mean is lower than the median, indicating a left-skewed distribution with a longer tail towards lower values.

- **Slightly Right-Skewed Distribution for GII 2010:** The mean is higher than the median, suggesting a slight right skew with a longer tail towards higher values.
  
> [!IMPORTANT]
> - **Imputation Method:** Given the varying skewness observed across different years for GII, using the **median** for imputation is a suitable choice


**6. Addressing the null values in the [LFPR_F] fields.**

![image](https://github.com/user-attachments/assets/a5c3221b-ba9a-4adf-b7f7-e84551f9d5a8)

*Null values were observed in the data for all years.*

- **Nearly Symmetrical Distributions**:
  1. 2000, 2005, 2010, and 2015: The mean is nearly equal to the median for the selected years , indicating a balanced spread of values.
  2. 2020: The mean and median have a small difference, still suggesting a relatively balanced distribution.
> [!IMPORTANT] 
> - **Imputation Method**: Despite the nearly symmetrical distributions observed, the **median** is preferred for imputation.


**7. Addressing the null values in the [LFPR_M] fields.** 

![image](https://github.com/user-attachments/assets/ed8a0adc-ee70-4781-b98f-41a6048e4e1e)

- **Nearly Symmetrical Distributions for 2000, and 2005**:
    1. 2000: Mean and Median are nearly equal, indicating a 
    2. 2005:  Fairly symmetrical.
       
- **Clear Normal Distribution**:
   1. 2010: Mean and Median are equal, indicating a perfectly symmetrical distribution.

- **Slight Left-Skewed Distributions for 2015 and 2020**.
    1. 2015: Mean is slightly higher than the median, suggesting a near-normal distribution with a minor left skew.
    2. 2020: Mean is slightly higher than the median, indicating a slight right skew.
       
 > [!IMPORTANT]      
 > - **Imputation Method**: Given the observed right skew in the distributions for 2015 and 2020, and considering that 2010 had a normal distribution, I will impute the null values with the **median**. Even though 2010 exhibited a normal distribution there could be variations in skewness across the remaining years in the dataset. 
 

 ### 🐍 Implementation with Python:

> [!NOTE]
> I implemented a script that automates the process of analyzing and visualizing multiple columns, thus eliminating the need to manually repeat the same steps for each column. This script not only streamlines the workflow but also effectively integrates data analysis with visualization. It calculates important statistics such as skewness and determines the appropriate imputation method for missing values. Additionally, it generates histograms for each column, complete with annotations that provide context about the data distribution and imputation choices. :joy:

My script in Python is: 

```ruby
# Identify columns with null values
null_columns = df.columns[df.isnull().any()]

# Combined function to check distribution, plot histogram, and calculate skewness
def analyze_column(column):
    print(f"\nProcessing column: {column}")
    print(f"Data type: {df[column].dtype}")
    print(f"Number of non-null values: {df[column].notnull().sum()}")
    
    if df[column].dtype not in ['int64', 'float64']:
        print(f"Skipping non-numeric column: {column}")
        return None, None

    if df[column].notnull().sum() > 0:
        skewness = skew(df[column].dropna())
        imputation_value = df[column].mean() if abs(skewness) < 0.5 else df[column].median()
        
# Print skewness and imputation details before plotting! I tried to have things organized and all printed info presented together on top of the Histogram.
        print(f'Skewness of {column}: {skewness:.6f}')
        print(f'Imputed {column} with {"mean" if abs(skewness) < 0.5 else "median"}: {imputation_value}')

# Plot the histogram
        plt.figure(figsize=(5, 3))
        ax = df[column].plot(kind='hist', bins=10, edgecolor='black', color='#4527A0')
        plt.title(f'Distribution of {column}')
        plt.xlabel(column)
        plt.ylabel('Frequency')
        
        plt.text(
            x=0.98, y=0.95,
            s=f'Skewness: {skewness:.2f}', 
            ha='right', va='top',
            transform=ax.transAxes,
            fontsize=9, color='black',
            bbox=dict(facecolor='white', alpha=0.7, edgecolor='none')
        )
        plt.show()
        
        return skewness, imputation_value
    else:
        print(f"No non-null values to plot for column: {column}")
        return None, None

# Function to impute nulls based on skewness
def impute_nulls(column):
    print(f"\nImputing column: {column}")
    
# Get skewness and plot histogram
    skewness, imputation_value = analyze_column(column)
    if skewness is None:
        print(f"Skipping imputation for {column} as no valid skewness value.")
        return
    
    # Perform imputation
    df[column].fillna(imputation_value, inplace=True)
    print(f'Imputed {column} with {"mean" if abs(skewness) < 0.5 else "median"}: {imputation_value}')

# Apply imputation to each column with null values
print("Starting imputation process...")
for column in null_columns:
    impute_nulls(column)

# Verify there are no more null values
print("\nRemaining null values in each column:")
print(df.isnull().sum())

# Example of calling the function for a specific column
print("\nAnalyzing specific column:")
analyze_column('hdi_2005')
```

![image](https://github.com/user-attachments/assets/ea9e899e-e80b-47a9-96bd-79a2b693a9f2)

![image](https://github.com/user-attachments/assets/089a4392-2d99-415c-95e6-e010cd70a291)



 
# Conclusions on: 📊 vs 🐍 for Checking Distribution & Imputing Nulls.

> [!NOTE]
> I explored imputation methods for handling missing values using Power BI and Python. While both approaches aimed to address null values effectively, **the Python method demonstrated clear advantages in automation, consistency, and efficiency.**

> **Power BI Approach:**

> Detailed Manual Analysis.

  Steps Involved:
 - Plotted histograms to understand data distribution.
 - Used IQR method for outlier detection.
 - Visual verification with scatterplots.
 - Chose imputation methods based on data distribution (mean for symmetrical, median for skewed).
   
> [!TIP] 
> **While thorough, providing a clear visual understanding of data distribution, this method was time-consuming and prone to subjective interpretation and hunman bias.**

> **Python Approach:**

> Automated Analysis.

   Steps Involved:
  - Identified columns with null values.
  - Function to check distribution and calculate skewness.
  - Plotted histograms for visual confirmation.
  - Automated imputation based on skewness:
  - Mean for symmetrical distributions (|skewness| < 0.5).
  - Median for skewed distributions (|skewness| ≥ 0.5).
    
> [!TIP]     
> **Ensured consistent and objective imputation across all columns, saving time and reducing potential errors.**

> [!IMPORTANT]
> Power BI is ideal for users who prefer a visual, hands-on approach and are working with smaller datasets where detailed manual inspection is feasible.
> Python is best suited for users who require an efficient, consistent, and automated process, especially when dealing with large datasets.





# Development Indicators table

## Exploratory Data Analysis 

> [!IMPORTANT]   
> 1. The analysis is focused on the **21st century**. Any non related column was removed. 

2. **Erros & Data Completness**:
   + There were no errors.
   + There were Nulls:
     
     - Birth rate, crude (per 1,000 people): 8%
     - Death rate, crude (per 1,000 people): 8%
     - Electric power consumption (kWh per capita): 48%
     - GDP (USD): 5%
     - GDP per capita (USD): 5%
     - Individuals using the Internet (% of population): 10%
     - Infant mortality rate (per 1,000 live births): 11%
     - Life expectancy at birth (years): 11%
     - Population density (people per sq. km of land area): 1%
     - Unemployment (% of total labor force) (modeled ILO estimate): 13%
    
 3.  **Data Consistency**:

      + The data has been reviewed for consistency, and no significant issues were identified. All columns, including GDP and other economic indicators, are consistent and aligned with expected values.

        However, please note that I was unable to fully validate the GDP per capita (USD) values because the dataset does not include a direct population column. GDP per capita is calculated as GDP divided by the total population, and without the population data, I could not verify the accuracy of this metric.


 ## Cleaning Process with Python 

  * The field names listed above have been renamed to shorter versions.

   ```ruby
## Changing Column Names 

new_col_names = {
   'Birth rate, crude (per 1,000 people)': 'Birth %',
    'Death rate, crude (per 1,000 people)' : 'Death %',
    'Electric power consumption (kWh per capita)' : 'Electric Power Consumption',
    'Individuals using the Internet (% of population)': 'Population % using Internet',
    'Infant mortality rate (per 1,000 live births)' : 'Infant mortality %',
    'Life expectancy at birth (years)': 'Life Expectacy',
    'Population density (people per sq. km of land area)': 'Population Density',
    'Unemployment (% of total labor force) (modeled ILO estimate)' : 'Unemployment %'
    
}

df.rename(columns=new_col_names, inplace=True)

df.head(3)
 ```

  * The [country]: Some country names were simplified for consistency and ease of use. For example, "Iran, Islamic Rep" was renamed to "Iran". This was done to standardize names and ensure uniformity across the dataset.

 ```ruby
 ## simplifying country names

country_rename = {
    'Bahamas, The': 'Bahamas', 
    'Egypt, Arab Rep.': 'Egypt',
    'Gambia, The': 'Gambia',
    'Hong Kong SAR, China': 'Hong Kong',
    'Iran, Islamic Rep.': 'Iran',
    'Korea, Rep.': 'South Korea',
    'Macao SAR, China': 'Macao',
    'Syrian Arab Republic': 'Syria',
     'Venezuela, RB': 'Venezuela',
    'Yemen, Rep.': 'Yemen'
}

df['Country Name'] = df['Country Name'].replace(country_rename)
```

  * [Region]:  I replaced the regional categories with their corresponding abbreviations to align with the format used in the HDI dataset. Consistency in naming conventions helps in merging and comparing data accurately.

 ```ruby
 ## Replacing Long Regions Names 

region_name = {
    'South Asia': 'SA',
    'Europe & Central Asia': 'ECA',
    'Middle East & North Africa': 'MENA',
    'East Asia & Pacific': 'EAP',
     'Sub-Saharan Africa': 'SSA',
    'Latin America & Caribbean': 'LAC',
    'North America': 'NA'
    
}

df['Region'] = df['Region'].replace(region_name)
```


  ## Addressing the null values

``` ruby
## Checking if Nulls :  found in 10 columns 

df.isna().sum()
```
![image](https://github.com/user-attachments/assets/10b2fa66-7423-4de8-9c58-8980a494b4b9)

> [!NOTE]
> The code follows the same logic as used for the HDI dataset, automating the process of analyzing and visualizing multiple columns in the development indicators dataset. This approach eliminates the need for repetitive manual steps and effectively integrates data analysis with visualization by calculating key statistics and generating annotated histograms. :wink:


``` ruby
# To Identify columns with null values
null_columns = df.columns[df.isnull().any()]

# A Combined function to check distribution, plot histogram, and calculate skewness
def plot_histogram(column):
    print(f"\nProcessing column: {column}")
    print(f"Data type: {df[column].dtype}")
    print(f"Number of non-null values: {df[column].notnull().sum()}")
    
    if df[column].dtype not in ['int64', 'float64']:
        print(f"Skipping non-numeric column: {column}")
        return None, None
    
    if df[column].notnull().sum() > 0:
        skewness = skew(df[column].dropna())
        imputation_value = df[column].mean() if abs(skewness) < 0.5 else df[column].median()
        
# Print skewness and imputation details before plotting. This is very important to improve the readability and presentation of data output!!! I HAVE TO BE HONEST I HAD SOME STRUGGLE WITH THIS PART!
        print(f'Skewness of {column}: {skewness:.6f}')
        print(f'Imputed {column} with {"mean" if abs(skewness) < 0.5 else "median"}: {imputation_value}')

# To Plot the histogram
        plt.figure(figsize=(3, 3))
        ax = df[column].plot(kind='hist', bins=10, edgecolor='black', color='#4527A0')
        plt.title(f'Distribution of {column}')
        plt.xlabel(column)
        plt.ylabel('Frequency')
        
        plt.text(
            x=0.97, y=0.95,
            s=f'Skewness: {skewness:.2f}', 
            ha='right', va='top',
            transform=ax.transAxes,
            fontsize=9, color='black',
            bbox=dict(facecolor='white', alpha=0.7, edgecolor='none')
        )
        plt.show()
        
        return skewness, imputation_value
    else:
        print(f"No non-null values to plot for column: {column}")
        return None, None

# Function to impute nulls based on skewness
def impute_nulls(column):
    print(f"\nImputing column: {column}")
    
# Get skewness and plot histogram
    skewness, imputation_value = plot_histogram(column)
    if skewness is None:
        print(f"Skipping imputation for {column} as no valid skewness value.")
        return
    
# Perform imputation
    df[column].fillna(imputation_value, inplace=True)
    print(f'Imputed {column} with {"mean" if abs(skewness) < 0.5 else "median"}: {imputation_value}')

# Apply imputation to each column with null values
print("Starting imputation process...")
for column in null_columns:
    impute_nulls(column)

# Verify there are no more null values
print("\nRemaining null values in each column:")
print(df.isnull().sum())

# Example of calling the function for a specific column
print("\nAnalyzing specific column:")
plot_histogram('Birth %')
```
![image](https://github.com/user-attachments/assets/b0ad100b-7b1d-4d0d-b019-724890ad777b)

![image](https://github.com/user-attachments/assets/dc4aedb4-8719-49bb-bcf2-49d81126f08c)


















     





    










     
