# World_Economic_Indicators

+ The dataset is sourced from the Maven Analytics platform: https://mavenanalytics.io/data-playground?order=date_added%2Cdesc&search=World%20Economic%20Indicators
## Research Questions: 
1. Which countries have experienced the highest growth in population and GDP? Is there overlap?

2. Where regions saw the most growth in HDI in the 21st century?

3. Which factors are highly correlated with life expectancy?

4. Which factors differentiate "High Income" vs "Low Income" Countries?

## Tools used :

Power BI 

## Dataset exploration 
+ The dataset contains 2 seperate Excel files :
1. Human Development Index:
   + **Column Num**: 1008
     ![image](https://github.com/user-attachments/assets/546c38a4-15e7-4322-bf6f-58b26136d0ee)
     
   + **Row Num**: 206
     
     ![image](https://github.com/user-attachments/assets/49c380f2-661d-4c20-82e3-e5b4cccc47c1)





2. Development Indicators:
   + **Column Num**: 15
     
      ![image](https://github.com/user-attachments/assets/88156a78-62e2-4c17-94b1-3aabbebb160d)

     
      ![image](https://github.com/user-attachments/assets/c2ee2b2e-bce6-43d7-8129-bf7707080f9f)

   + **Row Num**: 4009
     
     ![image](https://github.com/user-attachments/assets/42cf9cf1-bf00-48e6-a0b1-4ea55181c83f)


## Cleaning 

### HDI

1. The analysis is focused on the **21st century**. Any non related column was removed:

    ![image](https://github.com/user-attachments/assets/9f1eb3ff-3c6d-4613-95ac-3662ab63f218)

    
1. **Erros & Data Completness**:
   + There were no errors.
   + There were Blanks and Nulls:
     * Blanks were found in the [hdicode] & [region]:

       ![image](https://github.com/user-attachments/assets/7e0ae7de-2f7e-49ef-8733-2a886d6fd424)

     * Nulls were found in the HDI year columns ranging from 2% - 10%.
    
       ![image](https://github.com/user-attachments/assets/e69ca14f-c785-4725-b446-d0bca3978fa7)

 2. **Data Consistency**:
     
     * The [ISO 3], a column that is expected to contain the three-letter codes for countries as defined by the ISO 3166-1 standard. However, in the current column there included the HDI Groupings and Regional Groupings as well.
    
       ![image](https://github.com/user-attachments/assets/c0b27f45-4aa3-4402-9df9-46eba1deadf1)

     * *HDI Groupings*: ZZA.VHHD: Very High Human Development | ZZB.HHD: High Human Development | ZZC.MHD: Medium Human Development | ZZD.LHD: Low Human Development

     * *Regional Groupings*: ZZE.AS: Asia | ZZF.EAP: East Asia and Pacific | ZZG.ECA: Europe and Central Asia | ZZH.LAC: Latin America and Caribbean | ZZI.SA: South Asia | ZZJ.SSA: Sub-Saharan Africa | ZZK.WORLD: World Aggregate
   
 ### HDI Data Preparation 

 + As mentioned the [ISO 3] contained the HDI Groupings and Regional Groupings. Taken that we have dedicated columns for the hdi codes and for regional categories, I filtered out the aforementioned rows from the [ISO 3] and cleaned the respective [hdicode] and [region] as follows:

   ![image](https://github.com/user-attachments/assets/e2f4f9d3-8388-464e-83d2-9b5bf5c387f5)

   #### Step 1:

     Is to clean the [hdicode]. To keep things organized, i removed the corresponding hdi codes nested in the [ISO 3]:
     
     ![image](https://github.com/user-attachments/assets/00ed5377-33ae-48e0-9135-7a33a15d83d5)

     The [hdicode] column contained a total of 15 blank rows. The emphasis is on the countries that have blank HDI codes (as the HDI and Regional codings will be filtered out eventually). To maintain consistency, I replaced the blanks with Null, and then with N/A. In addition, I replaced the more general categories: Low, Medium, High, Very High with the more informative codes as found earlier in the [ISO 3] (VHHD, HHD, MHD, LHD). 

     ![image](https://github.com/user-attachments/assets/69ba784f-4559-4e13-8503-40de22d68966)                  ![image](https://github.com/user-attachments/assets/fe15fc28-db2f-42db-9a02-b63c885a8b46)                                                                                              ![image](https://github.com/user-attachments/assets/506c62f5-843b-4038-a131-3d141d7606d1)

   ![image](https://github.com/user-attachments/assets/d4bd5c68-2c40-491e-8360-d8f9d42f2698)                                                                    ![image](https://github.com/user-attachments/assets/5e685cdc-f8bc-4695-b425-e3f505a5da37)


 
   A similar approach was followed for the [region] column, which contained 55 blank rows. However, instead of filling the blanks with N/A, I found it easier to identify the correct region for each country. Therefore, I filled the blanks with the appropriate region.
   
* I first created a new conditional column called [Region_filled], listing only the countries whose region was missing from the original [region] column:
      
 ![image](https://github.com/user-attachments/assets/af53f8e4-4781-406e-92c6-c24ce333ad1d)

* Then I used this conditional column to fill the blanks of the original region column: 

 ![image](https://github.com/user-attachments/assets/ba444660-76b9-4b1c-95d7-b42d6d795e3a)

 * Result: A complete [region] column was created, currently called as [Region_NO Blanks]. 

   ![image](https://github.com/user-attachments/assets/ed0833aa-6a0f-4249-9fee-ff795750c4f4)

 * To avoid redundancy: I removed the original [region] and the [Region Filled] column, and I only kept the [Region_NO Blanks] , which i renamed back to  [region].
   
 * Now, both the [hdicode] and [region] columns comply with the rules of consistency and readability.

   ![image](https://github.com/user-attachments/assets/f0688127-15b2-4523-8a37-3b7c6a715ca9)

 * Before moving forward, I clean the regional coding that was nested in the [ISO 3]:

   ![image](https://github.com/user-attachments/assets/80d85163-f6d0-4f6f-82cb-7c7dd5f3c030)


   #### Step 2:

   Is to address the null values in the HDI fields.

   Initially, I considered using the mode, but due to multiple values sharing the highest frequency in some HDI fields, a clear mode could not be determined. As an alternative, I opted to use either the average or the median as an imputation method. However, the mean is sensitive to outliers. Because, outliers can pull the mean towards them, making it less representative of the central tendency of the data. So, to proceed cautiously, I first had to check for outliers. But the distribution of the data will define first the method to use in order to detect outliers.

   * **If data follows Normal Distribution**: Z-score for detecting outliers.

   * **If data follows Non - Normal Distribution**: better to use methods that do not assume normality, such as the interquartile range (IQR) method or the percentile method.

   Approach followed for checking of distribution:

1.  Plotted Histograms with bin size 1%.  
  
      ![image](https://github.com/user-attachments/assets/7b071cd6-0d9e-46a0-8be1-7c9ae824744c)

- **Left-Skewed Nature**: All distributions are left-skewed, meaning that the majority of the data points (countries) have higher HDI values. However, a significant number of countries with lower HDI values (closer to 0.2-0.4) create a long tail to the left.
- **Mean vs. Median**: 1. The mean being lower than the median further confirms the left-skewed nature of the data.
                       2. Both the mean and median have increased over the years, indicating an overall improvement in HDI scores for the countries.
                       3. The gap between the mean and median shows a slight decrease by 2020, suggesting that the distribution is becoming more symmetrical (1). 
- **Consistency Over Years**: The general pattern remains consistent over the years, with slight improvements in HDI values (increasing mean and median).
- **Central Tendency Interpretation**: In left-skewed distributions, the median is typically a more accurate measure of central tendency than the mean because it is less affected by the long tail of lower values.
- **Outlier Detection**: Skewness influences the choice of outlier detection methods. The Interquartile Range (IQR) method is preferred since it does not assume normality and effectively identifies outliers in skewed distributions.

(1). Let’s be honest: after seeing the trend towards a more symmetrical distribution, I decided to check the data for 2021, the last year in my dataset. The mean is 0.72 and the median is 0.74, just like in 2020. Suggesting, that the progress might be getting stabilized in the most recent years.
  
  ![image](https://github.com/user-attachments/assets/25c704a8-6abf-467b-81a4-5db6c1bae861)

  

 #### Step 3:

 To unpivot the HDI and LE years! 















     





    



     
