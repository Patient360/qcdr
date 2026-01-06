## MSK Measure Set
This repo provides access to the shared MSK Measure set, and the risk adjustment models used to report clinical performance outcomes for MIPS.

## Getting Started
The MSK Measures are multi-performance rate measures consisting of both observed and risk adjusted data **All quality data submitted to CMS-QPP MUST include both risk adjusted data along with the observed patient outcomes for the reporting period**. Each measure allows for different valid survey instruments to be used to collect patient reported outcomes for evaluating and reporting clinical performance to CMS.


### Risk Adjusting Patient Outcomes Data
There are several ways to use the risk adjustment models. The first approach uses an Excel Workbook. The second approach uses the set of CSV (coefficients) tables. A third approach uses SQL. We'll walk through using all three methods.

* [Risk Adjustment - Method 1 - Excel Workbook](docs/risk-adjustment-workbook-example.md)
* [Risk Adjustment - Method 2 - CSV Tables](docs/risk-adjustment-csv-example.md)
* [Risk Adjustment - Method 3 - SQL Example](docs/risk-adjustment-sql-example.md)

### Preparing Data for Submission

Every year CMS publishes the submission schema for all measures approved by CMS for MIPS. You can access all schemas for all measures for each year by going to the [measures directory](https://github.com/CMSgov/qpp-measures-data/blob/develop/measures/) in the qpp-cms github repo.


Note because the IROMS measures are inverse by design, the "performanceMet" category represents those patients who failed to meet the MCID. Patients who met or exceeded the MCID are counted in "performanceNotMet" category. For more information about submitting measures to CMS, please checkout the [QPP Submission API Docs](https://cmsgov.github.io/qpp-submissions-docs/)

### MSK Measure Stewards
<img src="docs/limber-logo-transparent-3.png" height="100"/>  <img src="assets/patient360_logo_bkgd.jpg" height="100"/> 
