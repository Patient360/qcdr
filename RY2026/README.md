## MSK Measure Set for 2026

1.  **Download the workbook for the current reporting year.**
    * [2026 - MSK Measure Calculation Methodology](https://github.com/Patient360/qcdr/raw/main/RY2026/models/"2026%20MSK%20Measure%20Calculation%20Methodology_v260125.xlsx")
    
    The existing data shown on the first spreadsheet (**Patient Data**) are synthetic data generated for the purpose of example. Each row represents a patient record, and each record consists of patient data required to calculate the risk-adjusted performance score (adjusted met/not met).
    
    There is a set of corresponding spreadsheets that map to predictors of PM including their specific categories or values. These include:
    * Intercepts
    * Age
    * Admit Score (for functional MSK measures 1-5)
    * Admit Pain (for pain MSK measures 6-10)
    * Gender
    * Payer
    * Treatment Type
    * Duration

2.  **Open the spreadsheet.**
    You will notice there are separate columns for each outcome measure. The column labels consist of the name of the quality measure (MSK1-MSK10) followed by a period (`.`), the body region (Neck, Upper Extremity, Back, Lower Extremity, Knee, and Neck) followed by a period (`.`), and the name of the survey:
    
    * NDI, MDQ, QDASH, UE (PROMIS upper extremity), LEFS, PF (PROMIS physical function), HOOSJr, KOOSJr, KOS, and NPRS.
    
    The first column(s) are used to look up the appropriate category/value for a specific patient.
    
    **Note on Duration:** The duration is for duration of symptom (the number of days from injury or surgery to admission). Use the row where the patient's value lies between the "lower" and "upper" values. If the patient's number matches exactly, then use the row for which they match the "upper" value (e.g., if the duration is 14 days, use the row for 7 to 14 days rather than the 14 to 30-day row). If this value is missing/unknown because the exact date of injury is not known, then use the row with "Missing" in the lower and upper columns.

3.  **Patient Data Sections**
    Note that the **Patient Data** spreadsheet has three sections:
    * **Section 1:** Where patient data should be loaded.
    * **Section 2:** Includes raw and adjusted progression. In the first column (observed progression), the value of `1` should be entered if the MCID has been achieved or exceeded, or `0` when it has not been achieved.
    * **Section 3:** Setting the Scale value.

4.  **Set the 'Scale' Value**
    In the third section, set the `Scale` value. This indicates what survey to use for Risk Adjustment (RA). There are 19 survey options numbered 2 through 20.
    In this example, we set the Scale to `2` which maps to the Functional NDI measure.

5.  **Predictions**
    Predictions of PM rate for the sample population should then be automatically calculated, with values ranging from `0.0` to `1.0`. The spreadsheet uses a `VLOOKUP` to map the patient data to the appropriate coefficient values and calculate a risk-adjusted PM rate. Note that the equation for calculating the predicted PM and the `VLOOKUP` functions is set in the **Predicted Progression** column.

6.  **Adjusted Performance Logic**
    The patient-level adjusted performance is generated using the following logic:
    When the predicted probability of achieving the MCID (**Predicted Progression**) is greater than `0.3`, it is interpreted as a moderate to high probability of achieving this minimal change. No RA is applied since these are all patients that are expected to achieve the outcome.

### Preparing Data for Submission

Every year CMS publishes the submission schema for all measures approved by CMS for MIPS. You can access all schemas for all measures for each year by going to the [measures directory](https://github.com/CMSgov/qpp-measures-data/blob/develop/measures/) in the qpp-cms github repo.  For more information about submitting measures to CMS, please see the [QPP Submission API Docs](https://cmsgov.github.io/qpp-submissions-docs/).


