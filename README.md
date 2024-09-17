

# World Economic Indicators

+ The dataset is sourced from the Maven Analytics platform: https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=World%20Economic%20Indicators
  
#### 1. Research Questions 
1. Which countries have experienced the highest growth in population and GDP? Is there overlap?
   
2. How does population density growth impact GDP growth across countries from 2000 to 2018?

3. Which factors drive economic growth (GDP)? 
   
4. In which regions of the world did Human Development Index (HDI) grow the most during the 21st century?

5. Which factors are highly correlated with life expectancy?

6. Which factors differentiate "High Income" vs "Low Income" Countries?
   
7. How labor force participation rates (male and female) relate to GDP growth and GDP per capita?

8. How do CO2 emissions per capita in 2018 vary across different income groups?
   
9. Which countries had the highest CO2 emissions in 2018 within each income group?
    
10. What was the average annual growth rate of Greece's GDP over the period 2000-2018?

11. How did Greece’s GDP compare with those of other countries in the same region?

12. How has the unemployment rate in Greece changed between 2000 and 2018?



#### 2. Tools used 

Power BI, Python 

> [!NOTE]
> In this analysis, I aim to explore and compare the effectiveness of Power BI and Python in handling and analyzing data. I will focus particularly on the World Economic Indicators dataset that requires imputation techniques, using descriptive statistics to address missing values. By applying methods such as mean and median imputation, I will assess how each tool manages data preprocessing and its impact on the accuracy and reliability of the analysis. 
This comparative study will provide insights into the strengths and limitations of Power BI and Python in dealing with incomplete data and performing robust statistical analyses.

#### 3. Dataset exploration 
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

#### 1. Exploratory Data Analysis 

**1.** **Erros & Data Completness**:
   + There were no errors.
   + There were Blanks and Nulls:
     
  * Blanks were found in:
      1. **Hdicode** column
         
      2. **Region** column 

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
       
 #### 2. Cleaning Process with Power BI and Python 

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
    "UK": "United Kingdom",
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
    "Iran (Islamic Republic of)": "Iran",
    'Saint Vincent and the Grenadines': 'St. Vincent and the Grenadines',
    'Saint Kitts and Nevis': 'St. Kitts and Nevis',
    'Saint Lucia': 'St. Lucia'
       
}

df.loc[:, 'country'] = df['country'].replace(country_rename)
print(df['country'])
```

***
   * The **[hdicode]** column contained a total of 15 blank rows. To maintain consistency, I replaced the blanks with Null, and then with N/A. In addition, I replaced the more general categories: Low, Medium, High, Very High with the more informative codes as found earlier in the [ISO 3] (VHHD, HHD, MHD, LHD). 
***

 📊 **Power Query**: The process of handling NaN and replacing categories is straightforward with user-friendly interfaces for _replacing_ values and handling nulls. 

   ![image](https://github.com/user-attachments/assets/5e685cdc-f8bc-4695-b425-e3f505a5da37)


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

 **Implementation with Power Query**  📊:

   **1.** I first created a new conditional column called [Region_filled], listing only the countries whose region was missing from the original [region] column:
      
  ![image](https://github.com/user-attachments/assets/af53f8e4-4781-406e-92c6-c24ce333ad1d)

   **2.**  Then I used this conditional column to fill the blanks of the original region column: 

 ![image](https://github.com/user-attachments/assets/ba444660-76b9-4b1c-95d7-b42d6d795e3a)

   **3.**  The [Region_NO Blanks] column has been updated, and the previously blank entries are now filled with the corresponding region names. 

   ![image](https://github.com/user-attachments/assets/ed0833aa-6a0f-4249-9fee-ff795750c4f4)

**Implementation with Pandas** 🐍:

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


#### 3. Addressing the null values

   ##### A. Implementation with Power Query 📊:
    
   🔍 **A. HDI xxxx Fields** 

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


  🔍 **B. Rest Fields** 
   
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
 

 ##### B. Implementation with Python 🐍:

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



 
##### C. Conclusions on: 📊 vs 🐍 for Checking Distribution & Imputing Nulls.

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

#### 1. Exploratory Data Analysis 

> [!IMPORTANT]   
> 1. The analysis is focused on the **21st century**. Any non related column was removed. 

+ **Erros & Data Completness**:
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
    
 +  **Data Consistency**:

      + The data has been reviewed for consistency, and no significant issues were identified. All columns, including GDP and other economic indicators, are consistent and aligned with expected values.

        However, please note that I was unable to fully validate the GDP per capita (USD) values because the dataset does not include a direct population column. GDP per capita is calculated as GDP divided by the total population, and without the population data, I could not verify the accuracy of this metric.


 #### 2. Cleaning Process with Python 

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
    'Yemen, Rep.': 'Yemen',
    'Slovak Republic': 'Slovakia',
    "Cote d'Ivoire": "Côte d'Ivoire",
    'Czech Republic': 'Czechia' , 
    'Russian Federation': 'Russia',
    'Kyrgyz Republic': 'Kyrgyzstan', 
    'West Bank and Gaza': 'Palestine'
    
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
> [!WARNING]
> By replacing "North America" with "NA," I encountered a new issue: Pandas interpreted "NA" as a missing value and replaced it with NaN.

![image](https://github.com/user-attachments/assets/845f0270-871c-409e-94b5-d2ae98cb9502)

And as a matter of fact here we can see: 

![image](https://github.com/user-attachments/assets/0c5ba8d9-97e8-428a-8ba9-38e08c1f2cf8)

**Conclusion: I had to go back and replace "NA" with "NAM" to avoid confusion with NaN and ensure accurate data representation.**

 ```ruby
## Replacing Long Regions Names 

region_name = {
    'South Asia': 'SA',
    'Europe & Central Asia': 'ECA',
    'Middle East & North Africa': 'MENA',
    'East Asia & Pacific': 'EAP',
     'Sub-Saharan Africa': 'SSA',
    'Latin America & Caribbean': 'LAC',
    'North America': 'NAM'
    
}

## df['Region'] = df['Region'].replace(region_name)
df.loc[:, 'Region'] = df['Region'].replace(region_name)
 ```

#### 3. Addressing the null values with Python

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




# Exploratory Data Analysis (EDA) with Python 

1. **Initial Data Preparation:** I checked if both datasets contain the same country names

```ruby 
# Which country names in HDI but not in Development Indicators?
missing_in_dev_indicators = set(hdi_df['country']) - set(dev_indicators_df['Country Name'])
print("Countries in HDI but not in Development Indicators:")
print(missing_in_dev_indicators)

# Which country names in Development Indicators but not in HDI
missing_in_hdi = set(dev_indicators_df['Country Name']) - set(hdi_df['country'])
print("Countries in Development Indicators but not in HDI:")
print(missing_in_hdi)
```
![image](https://github.com/user-attachments/assets/ad72f14a-0447-4913-b66c-fd0b5b78675d)

2. **I proceeded to address the questions.**

## Question 1: Which countries have experienced the highest growth in population and GDP? Is there overlap?

#### 1. Bar Chart

```ruby
## Vizualizing the Top Countries with highest GDP & Population Density 

main_color = "#4527A0"
highlight_color = "green"

# style for the plots
sns.set(style="whitegrid")


fig, ax = plt.subplots(2, 1, figsize=(14, 12))

# Bar chart for Population Density Growth
palette_population = [highlight_color if country in overlap else main_color for country in top_population_growth.index]
sns.barplot(x=top_population_growth['Popul. Density Growth %'].index, 
            y=top_population_growth['Popul. Density Growth %'], 
            ax=ax[0], palette=palette_population)
ax[0].set_title('Top 10 Countries by Population Density Growth (2000-2018)')
ax[0].set_xlabel('Country')
ax[0].set_ylabel('Population Density Growth %')
ax[0].tick_params(axis='x', rotation=45)

# Bar chart for GDP Growth
palette_gdp = [highlight_color if country in overlap else main_color for country in top_gdp_growth.index]
sns.barplot(x=top_gdp_growth['GDP Growth %'].index, 
            y=top_gdp_growth['GDP Growth %'], 
            ax=ax[1], palette=palette_gdp)
ax[1].set_title('Top 10 Countries by GDP Growth (2000-2018)')
ax[1].set_xlabel('Country')
ax[1].set_ylabel('GDP Growth %')
ax[1].tick_params(axis='x', rotation=45)

# Highlighting overlapping countries with  a border around 
for country in overlap:
    # Population Density chart
    patch_index = top_population_growth.index.get_loc(country)
    ax[0].patches[patch_index].set_edgecolor('black')
    ax[0].patches[patch_index].set_linewidth(2)
    
    # GDP Growth chart
    patch_index = top_gdp_growth.index.get_loc(country)
    ax[1].patches[patch_index].set_edgecolor('black')
    ax[1].patches[patch_index].set_linewidth(2)

plt.tight_layout()
plt.show()
```

![image](https://github.com/user-attachments/assets/9e77df8d-5af1-43cd-aa12-bd9eb5368054)


#### 2. Conclusions

- Top 10 in population increase: Qatar, Eritrea, and the United Arab Emirates
- Top 10 in GDP increase: Eritrea, Faroe Islands, and Greenland  
- Overlap is observed for: Eritrea, Equatorial Guinea and Angola

This overlap indicates that these countries experienced both rapid growth in population density 
and significant economic expansion. 

## Question 2: How does population density growth impact GDP growth across countries from 2000 to 2018?
 
- To answer this question I used the column [GDP (USD)] and [Population Density] from the Development Indicators dataset.
  
#### 1. Data Filtering
- I focused on data from the years 2000 and 2018 to calculate the **percentage growth**, allowing for a clear comparison of long-term trends in **population density and GDP over nearly two decades**. This approach highlights significant changes without the complexity of year-by-year analysis.
  
```ruby
# To simplify the analysis, and identify long term growth patterns and overall change:
# I will focus on the start and end year of my dataset
# And will not count year to year fluctuations 

# Filtering the data for 2000 and 2018
filtered_data = dev_indicators_df[dev_indicators_df['Year'].isin([2000, 2018])]

# Pivoting, so that each country has its 2000 and 2018 data on the same row
pivot_data = filtered_data.pivot(index='Country Name', columns='Year', values=['Population Density', 'GDP (USD)'])

# Calculation of Growth Rate for both variables 
pivot_data['Popul. Density Growth %'] = (pivot_data['Population Density'][2018] - pivot_data['Population Density'][2000]) / pivot_data['Population Density'][2000] * 100
pivot_data['GDP Growth %'] = (pivot_data['GDP (USD)'][2018] - pivot_data['GDP (USD)'][2000]) / pivot_data['GDP (USD)'][2000] * 100

# Showing the results 
pivot_data[['Popul. Density Growth %', 'GDP Growth %']]
```
#### 2. Scatter plot:

```ruby
# Time for the scatterplot 

# Defining what will be outliers
gdp_threshold = 2500  # Updated threshold for GDP Growth
pop_density_threshold = 300  # Updated threshold for Population Density Growth

# Define colors
deep_purple = '#6a0dad'  # Deep purple for scatter plot dots
background_color = '#D1C4E9'  # Light lavender background color

# Filtering out the outliers
outliers = pivot_data[(pivot_data['GDP Growth %_'] > gdp_threshold) | 
                      (pivot_data['Popul. Density Growth %_'] > pop_density_threshold)]

# Plotting without annotations except for outliers
plt.figure(figsize=(5, 3))
sns.regplot(
    x='Popul. Density Growth %_', 
    y='GDP Growth %_', 
    data=pivot_data, 
    scatter_kws={'color': deep_purple, 's': 100, 'alpha': 0.7, 'edgecolor': 'k'}, 
    line_kws={'color': 'red', 'linewidth': 2},
    ci=None
)

plt.ylim(0, 3500)  # Adjust based on your data range


# Annotate only the outliers using the index as the country name
for idx, row in outliers.iterrows():
    plt.annotate(
        idx,  # 'Country Name' is the index of the DF: pivot_data, so i access it by calling the index. 
        (row['Popul. Density Growth %_'], row['GDP Growth %_']), 
        textcoords="offset points",
        xytext=(0, 10),  
        ha='center',
        fontsize=8,
        color='black'
    )

# Defining titles and labels
plt.title('Population Density Growth vs GDP Growth (2000-2018)', fontsize=10)
plt.xlabel('Population Density Growth (%)', fontsize=8)
plt.ylabel('GDP Growth (%)', fontsize=8)
plt.xticks(fontsize=6)  # adjusting the values on the x and y 
plt.yticks(fontsize=6)  


# Set plot background color with my favorite color 
plt.gca().set_facecolor(background_color)

# Show the plot
plt.show()
```
![Impact of Population Density Growth on GDP Growth (2000-2018)](https://github.com/user-attachments/assets/6ce8e080-44c2-4b57-8ed9-cce6e31fa9b0)


🔍 **Scatter plot Interpretation:** 

- The scatter plot suggests a **positive correlation** between population density growth and GDP growth, suggesting that, on average, countries with increasing population densities tend to have higher GDP growth.
- The **data points are widely spread around the trend line**, indicating that the correlation is not strong. Other factors likely contribute to GDP growth beyond just population density growth.
- The scatter plot shows that **points are clustered at lower growth**. The majority of countries in the scatter plot seem to be clustered at lower levels of both GDP growth and population density growth. This is typical for many countries where economic growth is steady but not explosive, and population density changes are gradual.
- Qatar and Eritrea stand as **notable outliers**.
- Qatar, in particular, stands out as having a notable increase in population density while having relatively modest GDP growth compared to other countries. This indicates that Qatar's economy, being largely driven by its oil wealth, remains steady, but the country’s rapid population growth is likely due to its attractiveness as a destination for foreign workers.
- Eritrea emerges presents an extraordinary GDP growth rate of approximately 2000%. This dramatic increase makes Eritrea an exceptional case in the dataset. Its remarkable GDP growth might be attributed to recent significant economic changes or exceptional circumstances. 

#### 3. Regression Analysis.

Even though the **scatter plot indicated a weak correlation**, **regression analysis is still important**. 
- It quantifies the relationship more precisely
- Checks for statistical significance
- Helps understanding how well the data fits to the model
- Allows to assess the impact of outliers.
  
```ruby
# The independent variable:
X = pivot_data[['Popul. Density Growth %_']]

# The dependent variable:
y = pivot_data['GDP Growth %_']

# Adding a constant to the model (intercept)
X_with_const = sm.add_constant(X)

# Fitting the OLS regression model
model = sm.OLS(y, X_with_const).fit()

# Printing the summary of the regression model
print(model.summary())
```

🔍 **Regression analysis Interpretation:**

![image](https://github.com/user-attachments/assets/55125be2-1f69-4dc6-80d8-21768e63deda)

![image](https://github.com/user-attachments/assets/c5ef00d2-803b-4cd7-9091-ac2ac520f4d4)

- **R-squared**: 0.102 indicates that about 10% of the variability in GDP growth is explained by population density growth. This is a                    modest proportion, suggesting that while there is some relationship, the model does not capture most of the variance                    in GDP growth. 

- **Adjusted R-squared**: 0.097, slightly lower than R-squared, further reinforces the limited explanatory power of the model.
    
- **F-statistic**: is 23.66 with a p-value of 2.26e-06, it means that the model is statistically significant. So, the relationship 
                   between population density growth and GDP growth is unlikely to be due to random chance.
    
- **const (Intercept)**: is 259.98. This means that if the population density growth were zero, the GDP growth would still be around 
                         259.98
    
- **Popul. Density Growth % (Predictor)**: is 2.3627 with a standard error of 0.486. So, if we had 1% increas in population density 
                                           growth, GDP growth would be expected to grow by 2.36%.
                                     
 
- **Model Fit**: The low R-squared suggests that the model does not fit the data particularly well. 
                 While the model’s predictor (Population Density Growth %) is statistically significant, it explains only a small  
                 portion of the variance in GDP Growth %.
    
- **Final Thoughts**: The model shows statistical significance, but the explanatory power is limited. There is positive relationship 
                     between population density growth and GDP growth. But the low R-squared value suggests that other variables or 
                     factors may be influencing GDP growth.

#### 4. Residual Analysis 

I performed residual analysis after noting the low R- squared  value to better assess the model's fit.

```ruby
import numpy as np
import scipy.stats as stats

# Calculating residuals and fitted values
residuals = model.resid
fitted_values = model.fittedvalues

# influence measures
influence = model.get_influence()
leverage = influence.hat_matrix_diag


plt.figure(figsize=(10, 7))

# Residuals vs. Fitted Values Plot
plt.subplot(2, 2, 1)
sns.scatterplot(x=fitted_values, y=residuals)
plt.axhline(y=0, color='r', linestyle='--')
plt.title('Residuals vs. Fitted Values')
plt.xlabel('Fitted Values')
plt.ylabel('Residuals')

# Normal Q-Q Plot
plt.subplot(2, 2, 2)
stats.probplot(residuals, dist="norm", plot=plt)
plt.title('Normal Q-Q Plot')

# Scale-Location Plot
plt.subplot(2, 2, 3)
sqrt_std_residuals = np.sqrt(np.abs(residuals / np.std(residuals)))
sns.scatterplot(x=fitted_values, y=sqrt_std_residuals)
plt.axhline(y=0, color='r', linestyle='--')
plt.title('Scale-Location Plot')
plt.xlabel('Fitted Values')
plt.ylabel('Sqrt(Standardized Residuals)')

# Residuals vs. Leverage Plot
plt.subplot(2, 2, 4)
sns.scatterplot(x=leverage, y=residuals)
plt.axhline(y=0, color='r', linestyle='--')
plt.title('Residuals vs. Leverage')
plt.xlabel('Leverage')
plt.ylabel('Residuals')

plt.tight_layout()
plt.show()
```
![a results](https://github.com/user-attachments/assets/616ba659-9208-49fa-b9b4-d0bea362247d)


🔍 **Residuals Interpretation** 

- Linearity: The Residuals vs. Fitted Values plot suggests potential non-linearity in the model.

- Normality: The Q-Q plot shows deviations from normality, particularly in the tails, indicating possible outliers or skewness.

- Homoscedasticity: Both the Residuals vs. Fitted Values and Scale-Location plots suggest heteroscedasticity, where residual variance changes with fitted values.

- Influential Points: The Residuals vs. Leverage plot shows a few high-leverage points, but they do not have a large influence on the model.
    
#### 5. Conclusions

- **Scatter Plot Insights**: The scatter plot indicates **a positive correlation** between population density growth and GDP growth, suggesting that, on average, countries with increasing population densities tend to have higher GDP growth. However, the data points are widely spread around the trend line, **which signals a weak correlation**. 
  
- **Regression Analysis Limitations**: The low R-squared value and residuals analysis reveal that the regression model, as it stands, **cannot effectively explain the relationship between GDP growth and population density growth**.

  **Therefore, population density growth alone is not a strong predictor. Economic growth is driven by a more complex set of factors, and focusing solely on population density growth provides limited insights. To better understand the drivers of GDP growth, it is essential to consider additional variables and refine the model for a more comprehensive analysis.**


## Question 3: Which factors drive economic growth (GDP)? 

The previous Regression analysis proved that population density growth explains only a small portion of the variability in GDP growth (low R-squared value). 
This suggests that while population growth might contribute to GDP growth, other factors are likely playing a much more significant role in driving economic growth.

To answer the question I will perform multiple regression analysis. 

#### 1. Multiple Regression 

```ruby
# independent variables and target variable are the following (based on my available data): 
X = merged_df[['Population Density', 'Life Expectacy', 'Population % using Internet', 'Unemployment %', 'Electric Power Consumption']]
y = merged_df['GDP (USD)']

# constant term for the intercept
X = sm.add_constant(X)

# Fitting 
model = sm.OLS(y, X).fit()

print(model.summary())
```

![image](https://github.com/user-attachments/assets/5f55490b-2d5e-46f4-aaf6-b454959a9ca7)

![image](https://github.com/user-attachments/assets/f31c1b2e-773c-4323-8461-f443c3adf1b0)

**Interpretation:**

- R-squared: 0.068 This means that the model explains only 6.8% of the variability in GDP.  

- F-statistic (53.09, p-value 2.45e-53): Both indicate that the model is statistically significant. At least one predictor variable has a significant impact on GDP.

Coefficients: 

- Population Density: The coefficient is negative, indicating that as population density increases, GDP decreases. It might reflect countries with smaller land areas and large populations. P-value (0.000) shows this variable is statistically significant.

- Life Expectancy: The coefficient is positive, indicating that higher life expectancy is associated
with higher GDP. P-value (0.008) shows this variable is statistically significant.

- Population % using Internet: The positive coefficient indicates that as internet usage increases, 
GDP also increases. P-value (0.000) shows this variable is highly statistically significant.

- Unemployment %: The negative coefficient indicates that higher unemployment rates are associated with lower GDP.
P-value (0.001) shows this variable is statistically significant.

- Electric Power Consumption: The positive coefficient suggests that higher electricity consumption is associated with higher GDP.
P-value (0.000) shows this variable is statistically significant.

Residuals (Omnibus and Jarque-Bera Tests):

- The Omnibus and Jarque-Bera tests for normality of the residuals show extreme deviations from normality (p-value = 0.000). This suggests that the residuals are not normally distributed, which can be a sign that your model has specification issues or missing variables.

- Skewness and Kurtosis: The high skewness (9.248) and kurtosis (107.712) values suggest the presence of outliers or extreme values that may be distorting the model.

- Condition Number (5.24e+04):

- A high condition number (above 30 is usually considered problematic) indicates potential multicollinearity or numerical instability in the model. This could mean that some of the predictor variables are highly correlated with each other, which can inflate the standard errors and make the model unstable.

#### 2. Variance Inflation Factor (VIF) analysis

```ruby
from statsmodels.stats.outliers_influence import variance_inflation_factor

# Calculate VIF for each independent variable
vif_data = pd.DataFrame()
vif_data["Feature"] = X.columns
vif_data["VIF"] = [variance_inflation_factor(X.values, i) for i in range(X.shape[1])]

print(vif_data)
```

![image](https://github.com/user-attachments/assets/2f26c74c-21b5-4702-92fb-5e915d743d4d)

**Interpretation:**

Multicollinearity isn’t our problem.!!!!!

All VIF values are below the threshold of 5, and none are above 10, indicating that the predictors are not highly correlated with each other. This means that multicollinearity is unlikely to be causing significant problems with the regression analysis.

#### 3. Residual Analysis 

```ruby
# Predictions from the model
y_pred = model.predict(X)

# Residuals
residuals = y - y_pred

# Plotting residuals
plt.scatter(y_pred, residuals)
plt.axhline(0, color='red', linestyle='--')
plt.title('Residuals vs Fitted Values')
plt.xlabel('Fitted Values')
plt.ylabel('Residuals')

plt.show()

# Histogram of residuals
plt.hist(residuals, bins=30)
plt.title('Residuals Distribution')

plt.show()
```

**Interpretation** 

- Residuals vs Fitted Values: The residuals increase as the fitted values increase. There are some strong non-linear patterns in the residuals. The increasing variance and non-linearity suggest that the model **suffers from heteroscedasticity** as it has non-constant variance of residuals.

So, a different technique is needed, maybe log transformations. 

- Residual Distribution 

Most values are on the left and a long tail is extended on the right, typical for right skew. 
Right-skewness indicates that for some data points, the actual GDP is much larger than what the model predicted.!!
So, the **residuals are not normally distributed**. 

#### 4. Log Transformation for the Target Variable - GDP 

```ruby
#  The new target variable for the regression is the Log_GDP and not the original GDP (USD). 
merged_df['Log_GDP'] = np.log(merged_df['GDP (USD)'])

# The independent variables (same as before)
X = merged_df[['Population Density', 'Life Expectacy', 'Population % using Internet', 'Unemployment %', 'Electric Power Consumption']]

# The new target variable - the log transformed: 
y = merged_df['Log_GDP']  

# Constant term for the intercept
X = sm.add_constant(X)

# Fit the regression model using the log-transformed GDP
model = sm.OLS(y, X).fit()

print(model.summary())
```

![image](https://github.com/user-attachments/assets/da555a20-110a-4cea-9bf0-db5134f85e2d)

![image](https://github.com/user-attachments/assets/2385d529-d4ba-4fd0-bfe8-1ae6081d9c91)

**Interpreatation:**

By all means I see some improvement finally! 

- R-squared: 26.4%! This means the independent variables explain about 26.4% of the variation in the log-transformed GDP.
        
But there is always a but : 26.4% is still relatively low. So, this suggests other factors not included in the model could
also be influencing GDP, which is not unexpected given the complexity of an economy.

- P- values of independent variables: All low, so significant! So they significantly contribute in explaining the GDP. 
    
- Coefficients:
    
The coefficients have changed in scale because now we predict the log of GDP, not the actual values.
Example, for each 1-unit increase in Life Expectancy, on average, the log of GDP increases by
0.0541, holding other variables constant.

The negative coefficient for Population Density and Unemployment % indicates that higher values
for these variables are associated with a reduction in the log of GDP.

- Residuals (Omnibus and Jarque-Bera Tests): The p- value is less than 0.05, so the
                                             **residuals are not normally distributed**.

- Durbin-Watson: It is still quite low (0.131), suggesting there **may still be autocorrelation
                 in the residuals.**
       
- Cond. No.: It remains high (5.24e+04), which could suggest **some multicollinearity or
             numerical instability.** 


#### 5. Results 

The final regression model, with a log transformation of GDP, explains 26.4% of the variability in GDP. While this is an improvement over the previous model, it still suggests that a significant portion of GDP variation is driven by factors not included in the model.

**Significant Factors:**

**1. Life Expectancy:** Positively correlated with GDP. As life expectancy increases, so does GDP.
**2. Population % using Internet:** A strong positive relationship with GDP, indicating that higher internet penetration drives economic growth.  
**3. Electric Power Consumption:** Positively related to GDP, suggesting that higher energy consumption is associated with economic development.
**4. Population Density:** Shows a negative correlation, meaning countries with higher population density tend to have lower GDP, potentially reflecting constraints in smaller or overpopulated countries.
**5. Unemployment %:** As unemployment increases, GDP decreases, reflecting the negative economic impact of joblessness.

The variable though with the higher impact on GDP is the **'Population % using Internet'**. This stems from the coefficient. The **'Population % using Internet'** exhibits the largest coefficient compared to the other variables. This suggests that a 1-unit increase in internet use has a more substantial effect on GDP compared to some other variables.

Internet access often has a more direct and visible impact on economic growth by facilitating **communication, trade, education, and innovation**. Hence, while other factors like life expectancy and power consumption are also positive contributors, their impact seems to be smaller in comparison.

**Model Diagnostics:**

**1. Residuals:** The residuals **are not normally distributed**, as evidenced by the Omnibus and Jarque-Bera tests (p-value < 0.05). This indicates potential model specification issues or missing variables.
**2. Heteroscedasticity:** Residual analysis showed non-constant variance, suggesting **heteroscedasticity**, which violates the assumption of homoscedasticity in linear regression.
**3. Multicollinearity:** No significant multicollinearity was found, as indicated by low VIF values.
**4. Autocorrelation:** The Durbin-Watson statistic is quite low (0.131), pointing to possible **autocorrelation in the residuals**.
**5. Condition Number:** The high condition number (5.24e+04) suggests **potential multicollinearity** or numerical instability in the model, which may need further attention.

#### 6. **Conclusions**

The current model offers valuable interpretations and highlights key drivers of GDP growth:

1. Population using Internet
2. Life Expectancy
3. Electric Power Consumption
4. Unemployment
5. Population Density

The strongest positive driver of GDP growth is internet usage.
Life expectancy and electric power consumption also have positive relationships with GDP growth.
Unemployment and population density are negatively associated with GDP growth.

The analysis underscores the importance of technological development (internet usage) and human capital (life expectancy) in driving economic growth. Despite these valuable insights, the model also reveals the inherent complexity of economic growth and suggests that further refinement and exploration could enhance our understanding.


## Question 4: In which regions of the world did Human Development Index (HDI) grow the most during the 21st century?


#### 1. Avg HDI Growth grouped by region.

```ruby
hdi_df['hdi_growth'] = hdi_df['hdi_2021'] - hdi_df['hdi_2000']

# I will exclude the "World" region
hdi_df_filtered = hdi_df[hdi_df['region'] != 'World']

region_growth = hdi_df_filtered.groupby('region')['hdi_growth'].mean().sort_values(ascending=False)

# Step 3: Display the regions with the most growth
print(region_growth)
```

#### 2. Bar Graph 

```ruby
# setting my favorite color for highest growth with gradient for the rest
max_growth_color = '#4527A0'  # Deep purple
light_purple = '#D1C4E9'  # Light purple

# Finding the region with the highest growth
max_growth_value = region_growth.max()

# Creating a color list where the highest is deep purple, and others are lighter purples
colors = [
    max_growth_color if val == max_growth_value else 
    sns.light_palette("#4527A0", reverse=True, n_colors=len(region_growth))[i]
    for i, val in enumerate(region_growth)
]

# Plotting
plt.figure(figsize=(10, 6))
bars = plt.bar(region_growth.index, region_growth.values, color=colors)

# The title will be: 
plt.title('Average HDI Growth by Region (2000-2021)', fontsize=14)

# I dont want x and y axis labels
plt.xlabel('')
plt.ylabel('')

# Rotate x-axis labels for better readability and clarity 
plt.xticks(rotation=45)

# Save the plot
save_path = 'C:\\Users\\Mar\\Documents\\Data Analytics\\AProjects 2024\\World Economic Indicators\\hdi_growth_by_region.png'
plt.savefig(save_path, format='png', bbox_inches='tight')

# Time to show the plot
plt.tight_layout()
plt.show()
```


![image](https://github.com/user-attachments/assets/c284d08e-766a-466a-b8ff-26ff9311471b)


#### 3. Conclusions

- The chart shows that **South Asia (SA) had the highest HDI growth** from 2000 to 2021, 
while **Latin America and the Caribbean (LAC) had the lowest**. Other regions like Europe and Central Asia (ECA) and Sub-Saharan Africa (SSA) experienced moderate growth.



## Question 5: Which factors are highly correlated with life expectancy?

#### 1. Dataframes merging 

```ruby
merged_df = pd.merge(hdi_df, dev_indicators_df, on=['Country Name', 'Region'], how='inner')

print(merged_df.head())
```

#### 2. Correlation 

```ruby
from matplotlib.colors import LinearSegmentedColormap


columns_to_use = [
    'Life Expectacy', 'GDP per capita (USD)', 'Infant mortality %', 'Electric Power Consumption',
    'Unemployment %', 'Population % using Internet', 'Population Density', 'hdi_2021',
    'eys_2021', 'mys_2021', 'gnipc_2021', 'lfpr_f_2021', 'lfpr_m_2021', 'gii_2021'
]

# Simplified column names
simplified_column_names = {
    'Life Expectacy': 'Life Expectancy',
    'GDP per capita (USD)': 'GDP per Capita',
    'Infant mortality %': 'Infant Mortality',
    'Electric Power Consumption': 'Electric Power',
    'Unemployment %': 'Unemployment',
    'Population % using Internet': 'Internet Usage',
    'Population Density': 'Pop Density',
    'hdi_2021': 'HDI',
    'eys_2021': 'Exp Yrs School',
    'mys_2021': 'Mean Yrs School',
    'gnipc_2021': 'GNI per Capita',
    'lfpr_f_2021': 'Female Labor Force',
    'lfpr_m_2021': 'Male Labor Force',
    'gii_2021': 'Gender Inequality'
}

# a subset of the DataFrame and renaming the columns
subset_df = merged_df[columns_to_use].rename(columns=simplified_column_names)

# correlation matrix
correlation_matrix = subset_df.corr()

# With Life Expectancy (now renamed)
life_expectancy_corr = correlation_matrix['Life Expectancy'].sort_values(ascending=False)
print(life_expectancy_corr)

# Define a custom color map where deep purple represents strong positive correlation
colors = ["#ffffff", "#d1c4e9", "#4527A0"]  # White for weak, light purple for moderate, deep purple for strong positive
n_bins = 100  # Number of bins for the color map
cmap_name = "custom_purple"
custom_cmap = LinearSegmentedColormap.from_list(cmap_name, colors, N=n_bins)

plt.figure(figsize=(10, 8))
sns.heatmap(correlation_matrix, annot=True, cmap=custom_cmap, fmt='.2f', center=0, vmin=-1, vmax=1, linewidths=0.5)
plt.title('') 

plt.show()
```

**Resoning for using the above columns for the correlation analysis:**

- **From Development Indicators I used:**
   - Life Expectacy: It measures the average number of years a person is expected to live based on current mortality rates. It is a key indicator of health and quality of life. 
   - GDP per capita (USD): It represents the average economic output per person. Higher GDP per capita indicates higher income levels - better access to healthcare. 
   - Infant mortality %: A higher infant mortality rate indicates poorer health conditions and less effective healthcare systems, which directly impacts life expectancy negatively.
   - Electric Power Consumption: Higher consumption can be associated with better infrastructure and improved healthcare facilities. 
   - Unemployment %: Higher unemployment can be linked to lower quality of life.
   - Population % using Internet: Access to information and technology can influence health awareness, access to healthcare resources, and overall life quality.
   - Population Density: Population density might affect access to healthcare, pollution levels, and overall quality of life.

- **From Human Development Index(HDI) I used the most recent columns to reflect the latest trends:**
   - hdi_2021: HDI includes life expectancy, education, and income, and it should have a strong correlation with life expectancy.
   - eys_2021: It refers to the country's predicted years of schooling.
   - mys_2021: It refers to the country's average years of education.
   - gnipc_2021: The gross national income per person is an strong economic indicator.
   - lfpr_f_2021 + lfpr_m_2021: Female + Male  Labour Force Participation Rate. High rates, especially for women can indicate better access to resources.
   - gii_2021: Gender Inequality Index. Gender inequality can affect overall societal health


 #### 3. Conclusions  


 ![life_expectancy_corr_heatmap_purple](https://github.com/user-attachments/assets/2ac75898-b140-49f3-9df4-f2dee1e916d0)

   
**Strong Positive Correlations:** HDI, years of schooling (both average and expected), internet usage, and national income per capita are closely linked with higher life expectancy.

**Moderate Positive Correlations:** GDP per capita and electric power consumption show a moderate relationship with life expectancy.

**Strong Negative Correlations:** Gender inequality and infant mortality rates have strong negative impacts on life expectancy.

**Weak or No Significant Correlations:** Population density, unemployment, and labor force participation rates show weak or negligible correlations with life expectancy.



## Question 6: Which factors differentiate "High Income" vs "Low Income" Countries?

#### 1. Definition of Key Indicators 

```ruby
key_indicators = [
    'GDP per capita (USD)', 'Life Expectacy', 'Infant mortality %', 
    'Electric Power Consumption', 'Population % using Internet', 
    'Unemployment %', 'Population Density', 'hdi_2021', 'eys_2021', 
    'mys_2021', 'gnipc_2021'
]

# the mean for high-income countries
high_income_means = high_income_df[key_indicators].mean()


# the mean for low-income countries
low_income_means = low_income_df[key_indicators].mean()

print("High-income means:")
print(high_income_means)

print("Low-income means:")
print(low_income_means)
```

![image](https://github.com/user-attachments/assets/1abfe4df-7302-4509-bd05-8de3f97a26f4)

![image](https://github.com/user-attachments/assets/b612b72b-1377-4bb6-8ff8-e296ba4094bd)


#### 2. Bar Plot 

```ruby
# Finally i need to use log scale because the values for some indicators, like GDP per capita, are much bigger than others, like unemployment or infant mortality. 
# Without the log scale, the larger numbers  make the smaller ones hard to see on the chart.. 

    
# I need better column names for the plot
better_labels = [
    'GDP per Capita', 'Life Expectancy', 'Infant Mortality', 
    'Electric Power', 'Internet Usage', 'Unemployment', 
    'Pop. Density', 'HDI (2021)', 'Expected Yrs School (2021)', 
    'Mean Yrs School (2021)', 'GNI per Capita (2021)'
]

# Create the bar plot
plt.figure(figsize=(12, 8))
high_income_means.plot(kind='bar', color= '#4527A0', label='High Income')
low_income_means.plot(kind='bar', color= '#D1C4E9', label='Low Income', alpha=0.7)

# Set y-scale to logarithmic to handle the wide range of values
plt.yscale('log')

# Set labels, title, and other parameters
plt.ylabel('Mean Value (log scale)')
plt.title('')
plt.legend(title='Income Group')
plt.grid(axis='y', linestyle='--', alpha=0.7)

# I have to make the ticks to be aligned properly with the bars
ax = plt.gca()
ax.set_xticks(range(len(better_labels)))  
ax.set_xticklabels(better_labels, rotation=45, ha='right')  

# I adjust the layout for better fit
plt.tight_layout()

# Show the plot
plt.show()

```

![income_group_bar_plot_log](https://github.com/user-attachments/assets/9e9547e6-95fc-43eb-bf9a-0453f35608ad)


#### 3. Conclusions 

The bar plot reveals significant disparities between high-income and low-income countries across multiple key indicators. These results suggest that **high-income countries generally outperform low-income countries** across most indicators, especially in terms of economic strength, health, infrastructure, and education. However, unemployment seems to be higher in high-income countries.

**Economic Indicators:**

GDP per Capita and GNI per Capita (2021) are starkly higher in high-income countries, reflecting their stronger economic performance. In contrast, low-income countries show considerably lower values, emphasizing their financial challenges.

**Health Indicators:**

Life Expectancy is notably higher in high-income countries, pointing to better healthcare and living standards.
Infant Mortality is dramatically lower in high-income countries, suggesting better healthcare services for infants and pregnant women.

**Infrastructure and Technology:**

Electric Power Consumption and Internet Usage are significantly greater in high-income countries, reflecting better infrastructure and widespread access to technology. Low-income countries, by comparison, lag far behind, which could hinder their development.

**Education:**

The indicators for Expected Years of Schooling and Mean Years of Schooling are higher in high-income countries, indicating better access to and quality of education.

**Unemployment:**

Interestingly, Unemployment is slightly higher in high-income countries than in low-income ones, possibly reflecting differences in labor market structures or reporting mechanisms.

**Population Density:**

The population density difference is less pronounced but shows some variability. High-income countries exhibit greater density, likely reflecting urbanization trends, while low-income countries tend to be more rural.    


## Question 7: How labor force participation rates (male and female) relate to GDP growth and GDP per capita?
    
#### 1. Scater Plots

```ruby
sns.set(style='whitegrid')

# Line color
dark_gray_color = '#707070'  

# Plot 1: Labor Force Participation Rates vs. GDP Growth 
plt.figure(figsize=(14, 6))

# Plot Female Labor Force Participation with adjusted scatter and regression
plt.subplot(1, 2, 1)
sns.regplot(data=subset_df, x='lfpr_f_2018', y='GDP Growth', color='#4527A0', 
            scatter_kws={'s': 80, 'alpha': 0.7, 'edgecolor': 'w'},  
            line_kws={"color": dark_gray_color, 'linewidth': 1.5}, 
            ci=None)  # I prefer not to have confidence interval 
plt.title('Female Labor Force Participation vs. GDP Growth')
plt.xlabel('Female Labor Force Participation Rate (%)')
plt.ylabel('GDP Growth (%)')

# Plot Male Labor Force Participation 
plt.subplot(1, 2, 2)
sns.regplot(data=subset_df, x='lfpr_m_2018', y='GDP Growth', color='blue', 
            scatter_kws={'s': 80, 'alpha': 0.7, 'edgecolor': 'w'},  
            line_kws={"color": dark_gray_color, 'linewidth': 1.5},  
            ci=None)  
plt.title('Male Labor Force Participation vs. GDP Growth')
plt.xlabel('Male Labor Force Participation Rate (%)')
plt.ylabel('GDP Growth (%)')

plt.tight_layout()
plt.savefig(save_path_growth, format='png', bbox_inches='tight')
plt.show()

# Plot 2: Labor Force Participation Rates vs. GDP per capita 
plt.figure(figsize=(14, 6))

# Plot Female Labor Force Participation 
plt.subplot(1, 2, 1)
sns.regplot(data=subset_df, x='lfpr_f_2018', y='GDP per capita (USD)', color='#4527A0', 
            scatter_kws={'s': 80, 'alpha': 0.7, 'edgecolor': 'w'},  
            line_kws={"color": dark_gray_color, 'linewidth': 1.5},  
            ci=None)  
plt.title('Female Labor Force Participation vs. GDP per capita (2018)')
plt.xlabel('Female Labor Force Participation Rate (%)')
plt.ylabel('GDP per capita (USD)')

# Plot Male Labor Force Participation 
plt.subplot(1, 2, 2)
sns.regplot(data=subset_df, x='lfpr_m_2018', y='GDP per capita (USD)', color='blue', 
            scatter_kws={'s': 80, 'alpha': 0.7, 'edgecolor': 'w'},  
            line_kws={"color": dark_gray_color, 'linewidth': 1.5},  
            ci=None)  
plt.title('Male Labor Force Participation vs. GDP per capita (2018)')
plt.xlabel('Male Labor Force Participation Rate (%)')
plt.ylabel('GDP per capita (USD)')

plt.tight_layout()
plt.savefig(save_path_per_capita, format='png', bbox_inches='tight')
plt.show()
```

![lfpr_vs_gdp_growth_pretty](https://github.com/user-attachments/assets/28af3f88-5901-4dfa-92ef-a69386162fd4)


![lfpr_vs_gdp_per_capita_pretty](https://github.com/user-attachments/assets/ecc49323-c050-4c80-82a1-07abc19d3176)


#### 3. Conclusions 

**A. Female and Male Labor Force Participation vs. GDP Growth** 

 **- Female:**

1. Very weak positive relationship betweem female labor force and GDP growth.
2. The scatter points are clustered between 30% - 70%. 
3. There are many outliers, with some countries having very high GDP growth rates (above 1000%).

 **- Male:**
1. Weak positive relationship between male labor force and GDP growth.
2. The scatter points are clustered between 50% - 90%, while GDP growth remains in lower levels. This suggests that GDP is not really influenced by changes in male labor force participation.
3. There are many outliers. 


**B. Female and Male Labor Force Participation vs. GDP per Capita Growth** 

 **- Female:**
1. Very weak positive relationship betweem female labor force and GDP per Capita.
2. Most of the data points are concetrated between 30%-70% participation, and GDP per Capita ranges between 0$ - 175.000$.
3. Outliers are also observed when participation is arounf 50%-60% and GDP per capita over 175.000$.

 **- Male:**
 1. Very weak or almost neutral relationship. The line of best fit seems to be flat or moving slightly downward.
 2. Most data points are concetrated between 60%-80% of participation and GDP per Capita ranges between 0$ - 175.000$.

**Final thoughts:**
Weak correlations: The scatter plots show that there is weak correlation with GDP growth and GDP per capita. This indicates that while labor force participation may have some relationship with economic progress, **it is likely not the dominant factor influencing GDP growth and per capita income**. 

The high GDP growth and GDP per capita outliers may be linked to other factors - natural resources, trade, investements etc.

So, the current analysis suggests that simply increasing labor force participation rates will not lead to high GDP growth and high GDP per capita. 
     

## Question 8: How do CO2 emissions per capita in 2018 vary across different income groups?

#### 1. Box Plot 

```ruby
# The avg CO2 emissions by Income Group for 2018
avg_co2_by_income_2018 = merged_df.groupby('IncomeGroup')['co2_prod_2018'].mean().reset_index()

# Sort by avg CO2 to identify the group with the highest and second-highest emissions
avg_co2_by_income_2018 = avg_co2_by_income_2018.sort_values(by='co2_prod_2018', ascending=False)

# Red for the highest group, orange for the second-highest, purple for the middle group, and 
colors = ['#FF0000', '#FF7F0E', '#4527A0', '#4527A0', '#17BECF']  

colors.extend(remaining_colors)

# assigning incomeGroups to their respective color
income_color_map = dict(zip(avg_co2_by_income_2018['IncomeGroup'], colors))

# Step 4: Boxplot 
plt.figure(figsize=(10, 6))
sns.boxplot(data=merged_df, x='IncomeGroup', y='co2_prod_2018', palette=income_color_map)
plt.title('Distribution of CO2 Emissions by Income Group (2018)')
plt.xlabel('')
plt.ylabel('CO2 Emissions per Capita (tonnes)')
##plt.xticks(rotation=45)

# Finnaly I prefer straight x- labels: rotation to 0 and smaller font size
plt.xticks(rotation=0, fontsize=10) 

plt.tight_layout()

## I finally want the lables to look dif on the x axis : 

plt.ylabel('CO2 Emissions per Capita (tonnes)')

plt.show()
```

![co2_emissions_vs_income_group_pretty](https://github.com/user-attachments/assets/2e02e028-42f4-4904-be41-841eef677f8f)

#### 2. Conclusions 

**High-Income (nonOECD):**  
 - Is the group with the **highest emissions**. 
 - The **median** indicates assymetry in distribution: It is closer to the lower bound (around 6 tonnes) of the box: This shows that  there are **more countries with lower CO2 emissions**. But a few countries with significantly higher emissions are pulling the overall distribution upward, creating a wide spread of values in the upper range.

**High-Income: OECD:**
- Here half of the countries emit less than 8 tonnes of CO2 per capita.
- The spread of the middle 50% of countries (IQR) is more compact compared to the more variable, higher-emitting High-Income (nonOECD) countries.

**Upper Middle Income:**
-  Here half of the countries emit less than $ tonnes of CO2 per capita.
-  The **spread** of the middle half of the data ranges between 2-5 tonnes, but there are a few extreme outliers, showing that emissions vary significantly in this category.

**Lower Middle Income:**
- Here half of the countries emit less than 1 tonne of CO2 per capita.

 **Low Income:**
 - This group has the lowest emissions.
 - The median is near zero, indicating very low CO2 emissions per capita, with almost no outliers.

## Question 9: Which countries had the highest CO2 emissions in 2018 within each income group?

#### 1. Box Plot 

```ruby
### COLORS COLORS COLORS 

custom_palette = {
    'High income: nonOECD': '#FF0000',   # Red
    'High income: OECD': '#FF7F0E',      # Orange
    'Upper middle income': '#4527A0',    # Deep Purple
    'Lower middle income': '#4527A0',    # Deep Purple
    'Low income': '#A48BD0'               # Lavender
}


plt.figure(figsize=(14, 8))
##sns.barplot(data=plot_data, x='Country Name', y='co2_prod_2018', hue='Income Group', palette='tab10')


sns.barplot(data=plot_data, x='Country Name', y='co2_prod_2018', hue='Income Group', palette=custom_palette)

# I need annotations 
for p in plt.gca().patches:
    plt.annotate(format(p.get_height(), '.2f'), 
                 (p.get_x() + p.get_width() / 2., p.get_height()), 
                 ha='center', va='center', 
                 xytext=(0, 5), 
                 textcoords='offset points')

plt.title('Top CO2 Emission Outliers by Income Group (2018)')
plt.xlabel('')
plt.ylabel('CO2 Emissions per Capita (tonnes)')
plt.xticks(rotation=45, ha='right')  # i have to rotate a bit so that they fit better 
plt.tight_layout()


plt.savefig('C:\\Users\\Mar\\Documents\\Data Analytics\\AProjects 2024\\World Economic Indicators\\top_co2_emission_outliers_combined_plot.png', format='png', bbox_inches='tight')
plt.show()
```

![top_co2_emission_outliers_combined_plot](https://github.com/user-attachments/assets/609a3dbe-5df8-4036-8e41-87e4420c2e11)


#### 2. Conclusions 

- High-Income (nonOECD) – **Qatar & Trinidad and Tobago** stand out with extremely high emissions per capita, at 38.44 tonnes and 29.12 tonnes, respectively.

- High-Income (OECD)– **Australia, the United States, and Luxembourg** lead this group with emissions between 15-17 tonnes per capita. These values are lower than the highest nonOECD countries but still significant.

- Upper Middle Income  – **Kazakhstan and Mongolia** have the highest emissions in this group, with Kazakhstan leading at 17.32 tonnes. Other countries, like Turkmenistan, also show relatively high emissions, but they remain much lower than high-income countries.

- Lower Middle Income – **Ukraine and Zimbabwe** are among the top emitters in this group, though their emissions (5.24 tonnes for Ukraine) are far lower compared to the upper middle or high-income countries.

- Low Income – The lowest emitters, like **Cambodia and Benin**, have emissions less than 1 tonne per capita, demonstrating minimal CO2 output compared to wealthier nations.

- **Strong correlation between Income group and CO2 emissions per capita.**
- The highest CO2 emitters tend to be high-income countries, especially resource-rich ones like Qatar.
- Countries from lower income groups have significantly lower emissions. This emphasizes **global disparities in emissions based on economic status.**
- There are **notable outliers within each income group**, such as Kazakhstan for upper-middle income, showing the **uneven distribution of emissions even within the same income classification**.



## Question 10: What was the average annual growth rate of Greece's GDP over the period 2000-2018?

#### 1. Line graph 
```ruby
import matplotlib.pyplot as plt

# The df has to be sorted by Year
Greece_gdp = Greece_gdp.sort_values(by='Year')

# Ploting 
plt.figure(figsize=(12, 6))
plt.plot(Greece_gdp['Year'], Greece_gdp['GDP Growth Rate (%)'], marker='o', linestyle='-', color='#4527A0')

# Better to have annotations to show the greek economy in all it's drama 
for i, row in Greece_gdp.iterrows():
    plt.text(row['Year'], row['GDP Growth Rate (%)'], f"{row['GDP Growth Rate (%)']:.2f}", 
             ha='right', va='bottom', fontsize=9)

plt.title('Annual GDP Growth Rate of Greece (2000-2018)')
plt.xlabel('')
plt.ylabel('GDP Growth Rate (%)')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()

plt.show()
```

![greece_gdp_growth_rate](https://github.com/user-attachments/assets/2e728f63-a3b2-4ed6-a197-6aeac7eddb6e)


#### 2. Conclusions 

The word "economy" itself comes from the Greek word "οἰκονομία" (oikos + nemein), meaning "management of the household".  Quite ironic, isn’t it? As the very country that invented the term, one would think Greece would have had it all figured out. Yet, there’s another word Greece gave the world: "drama". And during the financial crisis, Greece certainly lived up to its reputation for dramatic flair.

**Volatile Growth:** The graph demonstrates Greece's volatile economic performance over this period, strongly tied to external and internal shocks, including the global financial crisis, the Eurozone debt crisis, and Greece's own fiscal troubles.

Greece experienced **significant growth in the early 2000s**, with the GDP growth rate peaking at 31.17% in 2004. This could have been influenced by preparations for the 2004 Athens Olympics, which involved substantial investment and infrastructure projects.

The **years following 2008 Greece's economy sharply declined**, with a growth rate falling to -6.77% in 2009.
The economic decline worsened during the Eurozone crisis, reaching its lowest point in 2011, with a -14.55% contraction.

The **years between 2010 - 2016 the growth rates were consistently negative**. This was a period marked by austerity measures, bailouts, and high levels of debt, which significantly impacted the Greek economy.

**After 2016** GDP growth rate were gradually following an **upward tragectory**. 

While Greece has shown signs of improvement, the steep declines and fluctuations underscore the importance of sustained economic reforms and growth strategies to prevent further downturns.

## Question 11: How did Greece’s GDP compare with those of other countries in the same region?

#### 1. Bar Chart 

```ruby
#years for comparison
selected_years = [2010, 2018]

gdp_subset = eca_data[eca_data['Year'].isin(selected_years)][['Year', 'Country Name', 'GDP (USD)']]

# Pivoting because i need countries as index and years as columns
gdp_pivot = gdp_subset.pivot(index='Country Name', columns='Year', values='GDP (USD)')

# colors
colors = {
    2010: 'lightgray',   # Color for 2010
    2018: '#4527A0'     # Deep purple for 2018
}

# And since Greece is the subject of research, is better to have a dif color 
greece_colors = {
    2010: '#FF6F61',    # Bright red for 2010
    2018: '#FF4C4C'     # darker red for 2018
}

# Plot  bar chart
fig, ax = plt.subplots(figsize=(12, 8))

# Width of bars
width = 0.35

# positions for bars
positions = list(range(len(gdp_pivot.index)))

# bars for each year
for i, year in enumerate(selected_years):
    # Define color for Greece and other countries
    bar_colors = [greece_colors[year] if country == 'Greece' else colors[year] for country in gdp_pivot.index]
    # Plot bars
    ax.bar([p + width * i for p in positions], gdp_pivot[year], width=width, color=bar_colors, edgecolor='black', label=f'GDP in {year}')

# And the labels, title, and legend
ax.set_title('GDP Comparison: Greece vs Other ECA Countries')
ax.set_xlabel('')
ax.set_ylabel('GDP (USD)')
ax.set_xticks([p + width for p in positions])
ax.set_xticklabels(gdp_pivot.index, rotation=45, ha='right')
ax.legend(title='Years')

plt.tight_layout()

plt.show()
```

![gdp_comparison_greece_vs_eca_shaded](https://github.com/user-attachments/assets/4c042fc9-1fae-4e82-8eff-384e46dbebf5)


#### 2. Conclusions  

**General Trend**: Most countries in this region have experienced GDP growth between 2010 and 2018, except for Greece, showing its distinct financial trajectory during the Eurozone crisis.

**Greece** (red):   Noticeable decline between 2010 to 2018, reflecting the economic impact of the debt crisis and subsequent austerity measures. While most countries show a GDP increase in 2018, Greece's economic struggles are evident.

**Other countries**: Large economies like **Germany**, **France**, and **United Kingdom** have a significant increase in their GDP, reaching into the trillions. Smaller economies like **Kazakhstan** and **Armenia** also see some growth, though at a much smaller scale.


## Question 12: How has the unemployment rate in Greece changed between 2000 and 2018?


#### 1. Line Graph 

```ruby
import pandas as pd
import matplotlib.pyplot as plt

# Sample data loading (replace this with actual data loading)
# merged_df = pd.read_csv('path_to_your_data.csv')

# Country under exam is Greece 
greece_unemployment = merged_df[merged_df['Country Name'] == 'Greece']

# Check if 2018 is in the data
if 2018 not in greece_unemployment['Year'].values:
    print("Year 2018 is missing from the data.")
else:
    # Plotting 
    plt.figure(figsize=(10, 6))
    plt.plot(greece_unemployment['Year'], greece_unemployment['Unemployment %'], marker='o', color='#4527A0', linestyle='-', linewidth=2)
    plt.title('Unemployment % in Greece')
    plt.xlabel('')
    plt.ylabel('')  
    plt.grid(True)
    
# Set all years on x-axis
    plt.xticks(range(2000, 2019))  
    
# Annotations to make the greek drama more readable 
    for i, row in greece_unemployment.iterrows():
        plt.annotate(f'{row["Unemployment %"]:.1f}%', 
                     (row['Year'], row['Unemployment %']), 
                     textcoords="offset points", 
                     xytext=(0,5), 
                     ha='center',
                     fontsize=9,
                     color='#4527A0')
    
    plt.tight_layout()

# Save the plot to the specified directory
save_path = 'C:\\Users\\Mar\\Documents\\Data Analytics\\AProjects 2024\\World Economic Indicators\\greece_unemployment_rate.png'
plt.savefig(save_path, format='png', bbox_inches='tight')

# Show the plot
plt.show()
```

![greece_unemployment_rate](https://github.com/user-attachments/assets/17bd540e-5546-4c65-9983-3c0dd2bd00b6)


#### 2. Conclusions  


 - **2000-2008**: The unemployment rate was relatively stable, fluctuating around 10% but gradually declining to 7.8% in 2008.
  - **2009-2013**: A steep increase in unemployment begins in 2009, coinciding with the global financial crisis and Greece's own debt crisis. Unemployment peaks at **27.5%** in 2013.
  - **2014-2018**: Following the peak, the unemployment rate slowly decreases year by year, reaching **19.2%** in 2018. **Despite the improvement, this is still much higher than pre-crisis levels.**



## Question 13: Which factors influenced Greece's GDP fluctuations and recovery between 2000 and 2018?

#### 1. Correlation Matrix 

```ruby
from matplotlib.colors import LinearSegmentedColormap

# Select relevant columns for correlation
columns_to_use = [
    'Life Expectacy', 'GDP per capita (USD)', 'Infant mortality %', 'Electric Power Consumption',
    'Unemployment %', 'Population % using Internet', 'Population Density', 
]

# Simplified column names
simplified_column_names = {
    'Life Expectacy': 'Life Expectancy',
    'GDP per capita (USD)': 'GDP per Capita',
    'Infant mortality %': 'Infant Mortality',
    'Electric Power Consumption': 'Electric Power',
    'Unemployment %': 'Unemployment',
    'Population % using Internet': 'Internet Usage',
    'Population Density': 'Pop Density',

}

# Filter the dataset for Greece
greece_data = merged_df[merged_df['Country Name'] == 'Greece']

# Select and rename the columns
subset_df = greece_data[columns_to_use].rename(columns=simplified_column_names)

# Compute the correlation matrix
correlation_matrix = subset_df.corr()

# Define a custom colormap with shades of purple
colors = ["#ffffff", "#d1c4e9", "#4527A0"]  # White for weak, light purple for moderate, deep purple for strong positive
n_bins = 100  # Number of bins for the color map
cmap_name = "custom_purple"
custom_cmap = LinearSegmentedColormap.from_list(cmap_name, colors, N=n_bins)

# Plot the heatmap with the custom colormap
plt.figure(figsize=(10, 8))
sns.heatmap(correlation_matrix, annot=True, cmap=custom_cmap, fmt='.2f', center=0, vmin=-1, vmax=1, linewidths=0.5)
plt.title('Correlation Matrix of Economic Indicators in Greece (2000-2018)', fontsize=13)

save_path = 'C:\\Users\\Mar\\Documents\\Data Analytics\\AProjects 2024\\World Economic Indicators\\greece_correlation_matrix.png'
plt.savefig(save_path, format='png', bbox_inches='tight')

plt.show()
```


![greece_correlation_matrix](https://github.com/user-attachments/assets/0924d4b3-51fd-4ee1-bb13-f211f45f8209)


#### 2. Conclusions 

- **Economic Growth & Well-being**: Higher GDP per capita is associated with better **health outcomes (lower infant mortality) and higher electric consumption**, reflecting development.
- **Unemployment**: Surprisingly, there's **a strong positive correlation between unemployment and internet usage**, likely reflecting a shift towards online services or education during high unemployment periods.
- **Population Density**: Positively correlates with GDP per capita and electric power, which are both typical indicators of economic development and urbanization.
