## Risk Adjustment - Method 1
Using the Excel Workbook.

1. Download the workbook for the current reporting year.

* [2024 - Risk Adjustment Workbook](../models/2024/01%20Example%20Excel%20Book.xlsx)

2. Open the workbook and look at the first sheet named, 'Patient Data'. This is where you input patient record data.

![](patient_sample.png)

The existing data shown here are synthetic data generated for the purpose of example. Each row represents a patient record, and each record consists of of both patient reported outcome measure response (e.g. the survey score), along with supplemntal patient data. There are a set of corresponding spreadsheets that map to predictors of FTP, these include:

* Intercepts
* Age
* Admit Score
* Admit Pain
* Gender
* Payer
* Treatment Type
* Duration

 Open each file. You will notice there are 1 or 2 or 3 or 4 columns for each outcome measure, the column labels consist of the name of the outcome measure (MSK01, MSK02, MSK03, MSK04, MSK05, MSK11, MSK12, MSK13, MSK14 and MSK15) followed by a period (".") and will notice there are 1 or 2 or 3 or 4 columns for each body region, the column labels consists of the name of the body region(Neck, Upper Extremity, Back, Lower Extremity, Knee and Neck) followed by a period (".") and will notice there are 1 or 2 or 3 or 4 columns for each Survey, the column labels consists of the name of the survey(NDI, PI, QDASH, UE, PENN, MDQ, LEFS, HOOSJr, KOS, PF, IKDC and NPRS).

The first column(s) are used to look up the appropriate row for a specific patient.

The duration is for duration of symptom, the number of days from injury or surgery to admission. Use the row where the patient's value lies between the "lower" and "upper" values, if the patients number matches exactly then use the row for which they match the "upper" value, e.g. if the duration is 14 days then use the row for 7 to 14 days rather than the 14 to 30-day row. If this value is missing/unknown because the exact date of injury is not known, then use the row with "Missing" in the lower and upper columns.

3. Next, set the 'Scale' value. This indicates what measure to use for the risk adjustment. There are 10 measure options numbered 2 through 11

![](set_measure.png)

In this example, we set the Scale to 2 which maps to the Functional ODI/MDQ measure.

4. Load sample of patient records. The patients included should have completed at least 1 patient reported outcome measure. Note: you can risk adjust patients who have completed at least 1 PRO, but assessing performance rates requires patients who have completed 2 or more PROs.

![](patient_sample_predictors.png)

5. Predict FTP rate for the sample population. Once the patient data has been inputted and the measure has been set, click enter on the spreadsheet to generate the predicted outcomes. The spreadsheet uses a VLOOKUP to map the patient data to the appropriate coefficient values, and calculate a risk adjusted FTP rate. Note that the equation for calculating the predicted FTP and the VLOOKUP function are set in the 'Predicted FTP' column.

![](patient_vlookup_prediction.png)

6. Assess Performance Rate Difference. Once we have a predicted failure to progress, we can now look at an actual patient population and determine how the predicted, or "adjusted" failure to progress compares to actual failure to progress, both at the individual patient level as well in the aggregate.

Calculate the mean of the predicted probabilities and the mean of the indicators (this second mean is just the proportion who failed to progress). Subtract the mean predicted value from the mean observed value and this is the adjusted value.

'Performance Rate Difference' = 'Observed FTP Rate' - 'Predicted FTP Rate'

![](performance_rate_difference.png)

A value of 0 (zero) is neutral and means that the failure to progress rate matched the predicted failure to progress rate exactly, a negative value means that the actual failure to progress rate was lower than predicted, so more patients in that group progressed than predicted. A positive value means that the observed rate was higher than predicted, so more patients failed to progress than would be predicted by their baseline scores. Below is an example group of patients:

![](patient_data.png)

Column B is the predicted values for each patient based on the formula and lookup tables above. Column C just indicates whether each patient failed to progress. For this clinic the predicted failure rate is 0.383 (38.3%) and the actual failure rate is 0.3 (30%) for a difference of -0.083 (-8.3%) meaning that they out performed expectation by 8.3%.

7. Scale Performance Rate Difference
Column M represents the individual patient level values for the Performance Rate Difference described above.

In order to report the Performance Rate Difference described above, we need to scale the values into a positive population level measure. Column N represents this value, and is calculated by taking the value in Column M and transforming into a positive number between 0.0 and 1.0 as `y = (x + 1) / 2`

![](scaled_performance.png)

This value represents the same measure as the `Difference (adjusted)` measure from step 6, but transformed into the numerator of a fraction at the population level for the population under consideration.


[Back Home](../README.md)
