::: {align="center"}
# 🧪 Data-Driven API Testing (DDT)

**Postman • Newman • Restful-Booker API**

Automated booking API tests using iteration data, dynamic variables, and
response assertions.

![Postman](https://img.shields.io/badge/Postman-API%20Testing-orange?logo=postman)
![Newman](https://img.shields.io/badge/Newman-CLI%20Runner-blue)
![Testing](https://img.shields.io/badge/Testing-Data--Driven-success)
:::

------------------------------------------------------------------------

## 📌 Project overview

This project demonstrates **Data-Driven Testing (DDT)** with Postman.
The collection reads booking details from an external data file through
`pm.iterationData`, stores values in environment variables, and
validates the API responses. The collection targets the public
Restful-Booker demo API. fileciteturn1file1L11-L45

**Base API:** `https://restful-booker.herokuapp.com`

## 🔍 Test scenarios

  -----------------------------------------------------------------------------
  Request                       Method                  Purpose
  ----------------------------- ----------------------- -----------------------
  CreateBooking                 POST                    Create a booking using
                                                        iteration data

  GetBookingIds                 GET                     Retrieve booking IDs

  GetBookingSpecificbookingid   GET                     Validate the details of
                                                        a booking

  UpdateBooking                 PUT                     Update booking details
                                                        with generated values

  DeleteBooking                 DELETE                  Delete a booking
  -----------------------------------------------------------------------------

The collection includes checks for status code, response time, response
size, and booking fields such as first name, last name, price, deposit
status, dates, and additional needs. fileciteturn1file1L57-L110

## 🛠️ Tools used

-   **Postman** --- API requests, pre-request scripts, and assertions
-   **Newman** --- command-line collection execution
-   **Newman HTML Reporter** --- HTML test report generation

## ▶️ Run the project

### 1. Install the tools

``` bash
npm install -g newman
npm install -g newman-reporter-html
```

### 2. Prepare the files

Import these into Postman:

-   `DDT_Collection.postman_collection.json`
-   `DDT_Enviroment.postman_environment.json`

**Data file required:** The collection reads its test values from an
iteration-data file. Create or add `DDT.csv` with these exact column
headings:

``` csv
firstname,lastname,totalprice,depositpaid,checkin,checkout,additionalneeds
```

Add one booking test record per row. The CSV must be included when
running the collection with Newman.

### 3. Run Newman and generate the HTML report

Run this command from the folder containing the collection, environment,
and CSV files:

``` bash
newman run "DDT_Collection.postman_collection.json" -e "DDT_Enviroment.postman_environment.json" -d "DDT.csv" -r cli,html --reporter-html-export "DDT_Report.html"
```

Open `DDT_Report.html` in a browser after the run finishes.

## 📸 Execution evidence

### Newman collection execution

![DDT Newman execution]("C:\Users\USER\Documents\DDT API testing\newman.png")

### HTML report file confirmation

![DDT HTML report
generated]("C:\Users\USER\Documents\DDT API testing\html.png")

## 📊 Recorded test run

The uploaded Newman Summary Report records the following run:

  Metric                            Result
  -------------------------- -------------
  Iterations                             1
  Requests                               5
  Assertions                            21
  Failed tests (dashboard)              13
  Skipped tests                          0
  Run duration                 2.3 seconds
  Average response time             381 ms

**Note:** The detailed assertion table reports 11 failed assertions,
while the dashboard displays 13 failed tests. Review the attached HTML
report for request-level details. These are recorded results from this
run, not a guarantee of future runs.

## 📁 Repository structure

``` text
DDT-API-Testing/
│
├── README.md
├── DDT_Collection.postman_collection.json
├── DDT_Enviroment.postman_environment.json
├── DDT.csv                         # Add your iteration data
├── DDT_Report.html
├── Newman Summary Report for DDT.html
│
└── DDT_screenshots/
    ├── ddt-newman-execution.png
    └── ddt-html-report-generated.png
```

## ⚠️ Before publishing

-   Include `DDT.csv` if you want others to reproduce the data-driven
    run.
-   Check the environment values before execution. In the uploaded
    environment, `fName` currently contains the API base URL; the
    collection's CreateBooking pre-request script overwrites it from the
    CSV iteration data. fileciteturn1file2L3-L8
-   Remove any real credentials, tokens, or private data before making
    the repository public.

------------------------------------------------------------------------

::: {align="center"}
**Built to practise data-driven API automation with Postman and
Newman.**
:::
