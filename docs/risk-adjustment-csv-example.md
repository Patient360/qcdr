## Risk Adjustment - Method 2
Using the CSV tables to generate risk adjusted patient data.

1. Download ALL CSV files listed in the coefficients subdirectory for a specific reporting year (typically this is the current reporting year).

* [2024 - Risk Adjustment Tables](../models/2024)

2. Open each file. You will notice there are 1 or 2 or 3 or 4 columns for each outcome measure, the column labels consist of the name of the outcome measure (MSK01, MSK02, MSK03, MSK04, MSK05, MSK11, MSK12, MSK13, MSK14 and MSK15) followed by a period (".") and will notice there are 1 or 2 or 3 or 4 columns for each body region, the column labels consists of the name of the body region(Neck, Upper Extremity, Back, Lower Extremity, Knee and Neck) followed by a period (".") and will notice there are 1 or 2 or 3 or 4 columns for each Survey, the column labels consists of the name of the survey(NDI, PI, QDASH, UE, PENN, MDQ, LEFS, HOOSJr, KOS, PF, IKDC and NPRS).

The first column(s) are used to look up the appropriate row for a specific patient.

The duration is for duration of symptom, the number of days from injury or surgery to admission. Use the row where the patient's value lies between the "lower" and "upper" values, if the patients number matches exactly then use the row for which they match the "upper" value, e.g. if the duration is 31 days then use the row for 0 to 30 days rather than the 31 to 90-days row. If this value is missing/unknown because the exact date of injury is not known, then use the row with "Missing" in the lower and upper columns.

The "intercepts" table has only 1 row of values, use the value from this row (and the appropriate column) for all patients.

Look up the appropriate value for each patient on each table, you should get 1 number from each table for each patient and sum up these values. Then put the sum into the following formula:

This is the predicted probability for failure to progress for that patient.

3. Set your sample patient population. In this case you can specify a single patient (row) for risk adjustment.
For example, if we have a patient who is a 43 year old Male, admitted with an MDQ score of 48 and a pain score of 7, who has commercial insurance, has 14 days since injury, and conservative treatment, then we would use the following values (these screenshots are for the example, the actual numbers may differ in the tables if the tables have been updated):

  Intercepts:

![](intercepts.png)

  Age:

![](age.png)

  Sex:

![](gender.png)

  Admit Score:

![](admit_score.png)

  Pain Score (at admit):

![](admit_pain.png)

  Payer (Insurance) type:

![](payer.png)

  Duration (days since injury/surgery):

![](duration.png)

  Treatment type:

![](treatment.png)

4. Predict Patient FTP Rate.  So for this example the sum would be:

```
x = -0.985615443700592 + 1.417297947 + 0 + -1.828403877 + 0 + 0 + 0 + 0.07409663711
```
where x sums to 0.2103819371643159. Using the summed value, you can then convert this to a probability value between 0.0000 and 1.0000.

```
p = EXP(x) / EXP(1+x)
```

So the final probability p, for failure to progress for this patient is 0.3678 or 36.78% chance of failure to progress.

5. Predict Patient FTP Rate for Entire Sample Population. Once you have tested and verified that you can generate predictions, you can now apply the same method to all patients.

6. Assess Performance Rate Difference. Once we have a predicted failure to progress, we can now look at an actual patient population and determine how the predicted, or "adjusted" failure to progress compares to actual failure to progress, both at the individual patient level as well in the aggregate.

Calculate the mean of the predicted probabilities and the mean of the indicators (this second mean is just the proportion who failed to progress). Subtract the mean predicted value from the mean observed value and this is the adjusted value.

```
'Performance Rate Difference' = 'Observed FTP Rate' - 'Predicted FTP Rate'
```

7. Scale Performance Rate Difference
As in the Workbook example, we now scale the performance rate difference into a measure in the range 0.0 to 1.0 by taking

`'Scaled Performance Rate Difference' = ('Performance Rate Difference' + 1) / 2`

This metric represents the same value as computed above, but scaled into a different range. The sum of this value at a patient level can be reported as the numerator of a population, in order to report the correct Performance Rate described in step 6.

[Back Home](../README.md)
