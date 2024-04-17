<img src="docs/keet-logo-color-white.png" height="25"/>  

## Keet Outcomes - Qualified Clinical Data Registry (QCDR)
This repo provides access to the shared MSK Measure set, and the risk adjustment models used to report clinical performance outcomes for MIPS.

## Getting Started
The MSK Measures are multi-performance rate measures consisting of both observed and risk adjusted data **All quality data submitted to CMS-QPP MUST include both risk adjusted data along with the observed patient outcomes for the reporting period**. Each measure allows for different valid survey instruments to be used to collect patient reported outcomes for evaluating and reporting clinical performance to CMS.


### Risk Adjusting Patient Outcomes Data
There are several ways to use the risk adjustment models. The first approach uses an Excel Workbook. The second approach uses the set of CSV (coefficients) tables. A third approach uses SQL. We'll walk through using all three methods.

* [Risk Adjustment - Method 1 - Excel Workbook]()
* [Risk Adjustment - Method 2 - CSV Tables]()
* [Risk Adjustment - Method 3 - SQL Example]()

### Preparing Data for Submission
The repo also provides the **measures descriptions** and **measures schemas** published by CMS every year since the MSK measures were approved by CMS. CMS publishes the **measures descriptions** and **measures schemas** every year on the QPP-CMS Github. Keet copies both the definitions and schema for each year and loads them here for ease.

* [Measures Overview]()
* [Measures Definitions/Schemas](measures)
