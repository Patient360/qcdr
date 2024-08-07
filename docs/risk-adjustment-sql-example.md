## Risk Adjustment - Method 3
Using SQL to calculate patients' probability of failure to progress. Follow the same steps in the Risk Adjustment - Method 2. Except in this case, you would load the CSV tables into a SQL DB and then use SQL to generate risk adjusted patient data.

* Download the CSV tables

* [2024 - Risk Adjustment Tables](../models/2024)

* Load the CSV tables into a SQL database
* Query sample patient population
* Query new Risk Adjustment Tables
* Run Prediction

Example SQL statement:

```sql
SELECT DISTINCT
                odi.ID,
                int.`MSK01.Neck.NDI` + admit.`MSK01.Neck.NDI` + pain.`MSK01.Neck.NDI` + age.`MSK01.Neck.NDI` + pyr.`MSK01.Neck.NDI` +
                sex.`MSK01.Neck.NDI` + txtype.`MSK01.Neck.NDI` + dur.`MSK01.Neck.NDI` AS `Predicted Score`
FROM intercepts AS int,
     `odi.test` AS odi
  LEFT JOIN admit ON odi.ADMIT_SCORE_NO = admit.ADMIT_SCORE_NO
  LEFT JOIN pain ON odi.ADMIT_PAIN_NO = pain.ADMIT_PAIN_NO
  LEFT JOIN age ON odi.AGE = age.`Age.num`
  LEFT JOIN pyr ON odi.pyr2 = pyr.pyr2
  LEFT JOIN sex ON odi.GENDER_DSC = sex.GENDER_DSC
  LEFT JOIN txtype ON odi.`TX_TYPE_CD` = txtype.`TX_TYPE_CD`
  LEFT JOIN dur ON odi.DurCat = dur.DurCat
;
```

[Back Home](../README.md)
