# Petstore API Tests – Newman

This repository contains API automation tests for **Swagger Petstore – Pet endpoints**
implemented using **Postman Collection** and executed via **Newman**.

The goal of this project is to demonstrate CRUD API testing (positive and negative scenarios)
and how to execute them locally with a visual HTML report.

---

## Prerequisites

Before running the tests, make sure the following tools are installed:

- **Node.js (LTS version)**  
  Download from: https://nodejs.org

After installation, verify in Command Prompt:

node -v  
npm -v

Both commands should return version numbers.

---

## Install Newman

Install Newman globally using npm:

npm install -g newman

Verify installation:

newman -v

If a version number is printed, Newman is installed correctly.

---

## Install HTML Reporter (Visual Report)

To generate a visual HTML report, install the htmlextra reporter:

npm install -g newman-reporter-htmlextra

This reporter generates a clean and readable HTML report suitable for manual review
and interview tasks.

---

## Project Files

Make sure the following files are located in the same folder:

- pettest.json  
  (Postman collection with API tests)

- pettestenv.json  
  (Postman environment file)

---

## Open Command Prompt in Project Folder

1. Open the folder that contains `pettest.json` and `pettestenv.json`
2. Click on the address bar of the folder
3. Type `cmd` and press Enter

Command Prompt will open directly inside that folder.

---

## Run Tests with Newman

Execute the tests using the following command:

newman run pettest.json -e pettestenv.json --reporters cli,htmlextra --reporter-htmlextra-export index.html

What this command does:
- Runs the Postman collection
- Uses the provided environment file
- Prints execution results in CLI
- Generates a visual HTML report named `index.html`

---

## View HTML Report

After the execution finishes:

1. Locate the generated `index.html` file in the same folder
2. Double-click the file or open it in any web browser

The report contains:
- Request list
- Assertions
- Pass / Fail status
- Execution details

---

## Test Coverage

The collection covers:

- Positive CRUD flow:
  - Create Pet
  - Get Pet by ID
  - Update Pet
  - Delete Pet
  - Get after delete (404 expected)

- Negative scenarios:
  - Get non-existing Pet
  - Invalid request payloads
  - Invalid status queries

Dynamic test data is used to avoid conflicts in the public Swagger Petstore environment.

---

## Notes

- Swagger Petstore is a public sandbox and may behave inconsistently at times
- Tests are designed to be re-runnable using dynamically generated pet IDs
- In a real production environment, stricter contract validation would be applied

---

## Quick Command Summary

Install Newman:  
npm install -g newman  

Install HTML reporter:  
npm install -g newman-reporter-htmlextra  

Run tests:  
newman run pettest.json -e pettestenv.json --reporters cli,htmlextra --reporter-htmlextra-export index.html
# petstore-newman-tests
