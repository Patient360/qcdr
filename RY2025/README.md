## MSK Measure Set for 2025
There are several ways to use the risk adjustment models. The first approach uses an Excel Workbook. The second approach uses the set of CSV (coefficients) tables. A third approach uses SQL. We'll walk through using all three methods.

* [Risk Adjustment - Method 1 - Excel Workbook](docs/risk-adjustment-workbook-example.md?raw=true)
* [Risk Adjustment - Method 2 - CSV Tables](docs/risk-adjustment-csv-example.md?raw=true)
* [Risk Adjustment - Method 3 - SQL Example](docs/risk-adjustment-sql-example.md?raw=true)

### Preparing Data for Submission

Every year CMS publishes the submission schema for all measures approved by CMS for MIPS. You can access all schemas for all measures for each year by going to the [measures directory](https://github.com/CMSgov/qpp-measures-data/blob/develop/measures/) in the qpp-cms github repo.


Note because the IROMS measures are inverse by design, the "performanceMet" category represents those patients who failed to meet the MCID. Patients who met or exceeded the MCID are counted in "performanceNotMet" category. For more information about submitting measures to CMS, please checkout the [QPP Submission API Docs](https://cmsgov.github.io/qpp-submissions-docs/)

