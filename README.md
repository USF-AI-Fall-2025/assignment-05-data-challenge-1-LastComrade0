# x62-data-challenge-student-pathways

## 1.Data Exploration

- Data quality: Data type
  - Categorical(object): DISTRICT_TYPE, DISTRICT_NAME, ACADEMIC_YEAR, DEMO_CATEGORY, STUDENT_POPULATION, AWARD_CATEGORY

  - Numeric (float64): DISTRICT_CODE, WAGE_YEAR1, WAGE_YEAR2, WAGE_YEAR3, WAGE_YEAR4

  - Missing Data
    - Only DISTRICT_CODE has missing values: 2,745 (13.26% of records) [Visualization 1]

- Range:
  - Categorical Columns - Unique Values: [Visualization 2]
    - DISTRICT_TYPE: 3 values (School District, Legislative District, All)
    - DISTRICT_NAME: 692 unique district names
    - DEMO_CATEGORY: 5 values (Race, Homeless Status, All, Foster Status, Gender)
    - STUDENT_POPULATION: 15 values (including "None Reported", "All", and specific demographic groups)
    - AWARD_CATEGORY: 4 values (Bachelor's Degree - Did Not Transfer, Associate Degree, Community College Certificate, Bachelor's Degree - Transferred)

  - Numeric Columns - Ranges: [Visualization 3]
    - DISTRICT_CODE: Min 110,017, Max 5,872,769, Mean 3,041,331, Median 3,166,852
    - WAGE_YEAR1: Min 0, Max $97,993, Mean $4,476, Median $0
    - WAGE_YEAR2: Min 0, Max $132,847, Mean $6,076, Median $0
    - WAGE_YEAR3: Min 0, Max $146,728, Mean $7,311, Median $0
    - WAGE_YEAR4: Min 0, Max $153,910, Mean $8,531, Median $0

  - Normal Distribution: [Visualization 3]
    - None of the numeric columns are normally distributed (p-value < 0.05 for all Shapiro-Wilk tests)
    - Wage columns are right-skewed (median = 0, many zeros)

- Semantics
  - Meaning of Columns:
    - DISTRICT_TYPE: Type of administrative district (School District or Legislative District)
    - DISTRICT_NAME: Specific name of the district
    - DISTRICT_CODE: Unique identifier for districts (missing for Legislative Districts)
    - ACADEMIC_YEAR: Academic year of the data (2018-2019)
    - DEMO_CATEGORY: Demographic classification category
    - STUDENT_POPULATION: Specific demographic group within the category
    - AWARD_CATEGORY: Type of educational credential earned
    - WAGE_YEAR1-4: Annual wages in years 1-4 after graduation
  
  - Column Relationships
    - DISTRICT_CODE and DISTRICT_NAME are related (one-to-one, but DISTRICT_CODE is missing for Legislative Districts)
    - DEMO_CATEGORY and STUDENT_POPULATION are hierarchical (STUDENT_POPULATION is a subcategory)
    - WAGE_YEAR1-4 form a time series tracking wage progression
    - The combination of district, demographic, and award category identifies unique student groups

- 562 Questions
    - Highest Wage Year 3 is Race - Asian: $61,497.25 average  [Visualization 5]
    - Lowest Wage Year 3 is Homeless Status - Experienced Homelessness in K-12: $42,112.33 average  [Visualization 5]

    - Negative Trends [Visualization 6]
      - There are 7 records with negative wage trends (WAGE_YEAR3 < WAGE_YEAR1)
      - Demographics:
        - Foster Status - Not Foster Youth: 3 records, average decline of $2,009.67 (from - $35,900 to $33,890)
        - Gender - Male: 2 records, average decline of $5,620 (from $59,361 to $53,741)
        - Race - Hispanic or Latino: 1 record, decline of $844 (from $28,199 to $27,355)
        - Race - White: 1 record, decline of $2,054 (from $66,051 to $63,997)
        - Bachelor's Degree - Did Not Transfer: 3 records, average decline of $2,836
        - Community College Certificate: 3 records, average decline of $2,847
        - Associate Degree: 1 record, decline of $3,117

    - Positive Trends [Visualization 5]
      - Majority show positive wage trend
      - Demographics:
        - Gender - Female: 421 records, average increase of $18,769 (from $28,087 to $46,856)
        - Foster Status - Not Foster Youth: 416 records, average increase of $19,543 (from $31,189 to $50,732)
        - Gender - Male: 409 records, average increase of $22,131 (from $37,188 to $59,319)
        - Race - Hispanic or Latino: 292 records, average increase of $17,473 (from $28,024 to $45,497)
        - Race - White: 243 records, average increase of $22,847 (from $33,465 to $56,312)
        - Homeless Status - Did Not Experience Homelessness in K-12: 236 records, average increase of $21,230 (from $32,554 to $53,784)
        - Race - Asian: 174 records, average increase of $23,516 (from $37,981 to $61,497)
        - All award categories show positive average wage growth
        - Bachelor's Degree holders (both transferred and did not transfer) show the strongest growth

