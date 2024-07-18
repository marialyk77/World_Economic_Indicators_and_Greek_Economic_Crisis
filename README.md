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
   + Column Num: 1008
     ![image](https://github.com/user-attachments/assets/546c38a4-15e7-4322-bf6f-58b26136d0ee)
     
   + Row Num: 206
     
     ![image](https://github.com/user-attachments/assets/49c380f2-661d-4c20-82e3-e5b4cccc47c1)





2. Development Indicators:
   + Column Num: 15
     
      ![image](https://github.com/user-attachments/assets/88156a78-62e2-4c17-94b1-3aabbebb160d)

     
      ![image](https://github.com/user-attachments/assets/c2ee2b2e-bce6-43d7-8129-bf7707080f9f)

   + Row Num: 4009
     
     ![image](https://github.com/user-attachments/assets/42cf9cf1-bf00-48e6-a0b1-4ea55181c83f)


## Cleaning 

### HDI

1. The analysis is focused on the 21st century. Any non related column was removed:

    ![image](https://github.com/user-attachments/assets/9f1eb3ff-3c6d-4613-95ac-3662ab63f218)

    
1. Erros & Data Completness:
   + There were no errors.
   + There were Blanks and Nulls:
     * Blanks were found in the [hdicode] & [region]:

       ![image](https://github.com/user-attachments/assets/7e0ae7de-2f7e-49ef-8733-2a886d6fd424)

     * Nulls were found in the HDI year columns ranging from 2% - 10%.
    
       ![image](https://github.com/user-attachments/assets/e69ca14f-c785-4725-b446-d0bca3978fa7)

   + Data Consistency:
     
     * The [ISO 3], a column that is expected to contain the three-letter codes for countries as defined by the ISO 3166-1 standard. However, in the current column there included the HDI Groupings and Regional Groupings as well.
    
       ![image](https://github.com/user-attachments/assets/c0b27f45-4aa3-4402-9df9-46eba1deadf1)

     * HDI Groupings: ZZA.VHHD: Very High Human Development | ZZB.HHD: High Human Development | ZZC.MHD: Medium Human Development | ZZD.LHD: Low Human Development

     * Regional Groupings: ZZE.AS: Asia | ZZF.EAP: East Asia and Pacific | ZZG.ECA: Europe and Central Asia | ZZH.LAC: Latin America and Caribbean | ZZI.SA: South Asia | ZZJ.SSA: Sub-Saharan Africa | ZZK.WORLD: World Aggregate




    



     
