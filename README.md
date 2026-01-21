
# QA Test Report: Evershop E-Commerce Application

## 1. Executive Summary
This repository documents the Quality Assurance (QA) lifecycle for the Evershop E-Commerce platform. The project scope included Requirement Analysis, Test Planning, Manual UI Testing, and Automated API Validation.

The primary objective was to validate the "Search" and "Shopping Cart" modules against specific client requirements, including fuzzy search logic, localization support, and inventory visibility.

**Project Status:** Completed
**Test Type:** Manual (Black Box) & API (Postman)

---

## 2. Repository Artifacts
The following files are included in this repository to provide full traceability of the testing cycle:

| File Name | Content Description |
|:---|:---|
| **Question-1.docx** | Requirement elicitation and client Q&A log[cite: 78]. |
| **Question 2 & 3.xlsx** | Comprehensive Test Suite for the Search feature (55 Test Cases). |
| **Question_4.xlsx** | Consolidated workbook containing UI Test Cases, API Test Cases, and Defect Reports[cite: 1, 3, 7]. |
| **Evershop api.postman_collection.json** | Automation scripts for backend API validation (Search and Cart endpoints). |
| **Test Feedback.docx** | Final test summary and executive sign-off[cite: 8]. |

---

## 3. Test Execution Metrics

### 3.1 Search Module Analysis
A total of 55 test cases were executed to validate the search algorithm's compliance with client specifications.

| Status | Count | Percentage | Description |
|:---|:---:|:---:|:---|
| **Passed** | 14 | 25.45% | Functionality works as expected. |
| **Failed** | 18 | 32.73% | Functionality contradicts requirements. |
| **N/A** | 23 | 41.82% | Blocked due to missing features (Category Filters, Voice Search). |
| **Total** | **55** | **100%** | |

### 3.2 Failure Root Cause Analysis
The failures in the Search module were mapped to specific unmet requirements:
1.  **Partial Match Failure:** The system fails to return results for partial keywords (e.g., "therm" or "steel")[cite: 27, 28].
2.  **Localization Failure:** The system does not support mixed-language queries (e.g., "Stil thermos") as requested by the client[cite: 53].
3.  **Spelling Error Tolerance:** Common spelling mistakes (e.g., "tharmos") result in zero search results[cite: 52].

---

## 4. Defect Report
The following defects were identified and logged during the testing cycle.

| ID | Module | Severity | Issue Summary | Status |
|:---|:---|:---|:---|:---|
| **BUG-01** | Search & Cart | N/A | No functional bug found in the happy path. | [cite_start]Closed [cite: 7] |
| **BUG-02** | Cart | **Low** | **Variant Display Issue:** When adding products with specific variants (e.g., White vs. Black), the cart displays the correct quantity but fails to visually distinguish the specific color variant selected. | [cite_start]**Open** [cite: 7] |

---

## 5. Technical Validation (API vs. UI)
Cross-layer testing was performed to ensure data consistency between the user interface and the backend API[cite: 17].

**Test Scenario:** Search for "Stainless Steel Thermos", Add 11 units to Cart, Verify Totals.

| Step | UI Result | API Result (Postman) | Verdict |
|:---|:---|:---|:---|
| **Search** | Product displayed correctly[cite: 1]. | GraphQL Query returned valid Product ID and SKU[cite: 4]. | **PASS** |
| **Add to Cart** | Item added with Quantity 11[cite: 2]. | REST POST request returned Status 200 OK[cite: 5]. | **PASS** |
| **Cart View** | Total Price validated as 385[cite: 2]. | API Response confirmed Total Price: 385[cite: 6]. | **PASS** |

---

## 6. Requirements Traceability
This testing cycle was grounded in the following requirements confirmed by the client:

* **R-01:** The search engine must support mixed languages (e.g., Banglish)[cite: 98].
* **R-02:** The system must highlight matching keywords in product descriptions[cite: 106].
* **R-03:** Out-of-stock products must remain visible in search results[cite: 95].
* **R-04:** Voice command support is required (currently missing)[cite: 107].

---

## 7. Author
**Name:** Oynndrila Singh Purkayestha 

**Role:** QA Engineer / Manual Tester

**Date:** 2026-01-15 
