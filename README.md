cat <<EOF > README.md
# Evershop E-Commerce Testing Project

## Project Description
This repository documents the Quality Assurance (QA) lifecycle for the Evershop E-Commerce platform, specifically focusing on the **Search** and **Shopping Cart** modules. The project involves Requirement Analysis, Test Planning, Manual Test Execution (UI), Automated API Testing, and Defect Reporting.

The primary objective was to validate the "Happy Path" user journey—searching for a specific product ("Stainless Steel Thermos"), adding it to the cart, and verifying the cart contents—while also rigorously stress-testing the Search algorithm against the client's specific requirements for fuzzy logic, mixed languages (Banglish), and special characters.

## Repository Structure & Artifacts

| File Name | Description |
|-----------|-------------|
| **Question-1.docx** | [cite_start]Requirement Analysis containing 10 high-priority questions posed to the client regarding search logic, localization, and UI behavior[cite: 82, 83]. |
| **Question 2 & 3.xlsx** | [cite_start]Comprehensive Test Suite for the Search Feature containing 55 detailed test cases with execution status[cite: 22]. |
| **Question_4.xlsx (UI)** | [cite_start]UI Test Cases covering the core "Happy Path" flow on the Chrome browser[cite: 1]. |
| **Question_4.xlsx (API)** | [cite_start]API Test Cases using Postman to verify backend logic matches UI behavior[cite: 3]. |
| **Question_4.xlsx (Defect)** | [cite_start]Defect Report logging issues found during execution, including severity and reproduction steps[cite: 7]. |
| **Evershop api.postman_collection.json** | Exported Postman Collection containing the GraphQL and REST requests used for backend validation. |
| **Test Feedback.docx** | [cite_start]Final executive summary of the testing cycle, confirming the end-to-end journey success[cite: 8]. |

---

## Requirement Analysis & Client Constraints
Before testing, a consultation was held to clarify the "Search" feature specifications. Key requirements confirmed by the client included:

1.  [cite_start]**Partial Match Support:** The system must support incomplete words (e.g., "therm" for "Thermos")[cite: 87, 88].
2.  [cite_start]**Mixed Language Support:** The system must handle "Banglish" (e.g., "Thermos bottol" or "stil flask")[cite: 96, 97].
3.  [cite_start]**Out of Stock Visibility:** Out-of-stock items must remain visible in search results[cite: 94, 95].
4.  [cite_start]**Voice Command:** The system is intended to support voice search in English and Banglish[cite: 107, 108].

---

## Test Execution Metrics

### 1. Search Module (Deep Dive)
A total of **55 test cases** were executed to validate the Search logic.
* **Total Executed:** 55
* **Passed:** 14 (25.45%)
* **Failed:** 18 (32.73%)
* [cite_start]**N/A (Blocked/Not Implemented):** 23 (41.82%)[cite: 22].

#### Critical Failure Analysis (Requirement vs. Actual)
Several high-priority requirements failed during validation:
* [cite_start]**Partial Search Failed:** Searching for "therm", "ermo", or "mos" resulted in "No results found," contradicting the client requirement for partial matching[cite: 27, 28, 29, 30].
* [cite_start]**Spelling & Localization Failed:** The system failed to handle common spelling mistakes (e.g., "Steel tharmos") and mixed language inputs ("Stil thermos"), which were explicit client requests[cite: 52, 53].
* [cite_start]**Highlighting Failed:** Search keywords were not highlighted in product titles or descriptions as requested[cite: 69, 70].

#### Blocked Scenarios (N/A)
Testing for "Voice Search" and "Category Filtering" was blocked because the features were not present in the current build:
* [cite_start]Voice search test cases (TC_50 to TC_55) were marked N/A due to the absence of a microphone icon[cite: 72, 73].
* [cite_start]Category-specific search (TC_01 to TC_05) was blocked as the homepage lacked category selection filters[cite: 23, 24].

### 2. Functional "Happy Path" (UI & API)
The core business flow was validated successfully across both UI and API layers.

**Test Data Used:**
* **Product:** Stainless Steel Thermos
* [cite_start]**Product ID:** 18 [cite: 5]
* [cite_start]**Quantity:** 11 [cite: 1, 5]
* [cite_start]**Unit Price:** 35 [cite: 1]

**Results:**
* **UI Testing:** 100% Pass. [cite_start]The user could successfully search, view, and add 11 items to the cart[cite: 1].
* **API Testing:** 100% Pass. The API correctly processed the request `{"sku":"THERMO-005-BLK","qty":2}` and returned the correct cart totals.

---

## Defect Report
A total of 2 defects were logged. One was closed as a non-issue, while one functional usability bug remains open.

| ID | Module | Severity | Summary | Status |
|----|--------|----------|---------|--------|
| **BUG-02** | Cart | Low | **Color variant (White) not validated separately.** When adding products with different variants, the cart displays the total quantity but does not visually distinguish between the Black and White variants in the list view. | [cite_start]**Open** [cite: 7] |

---

## Technical Details: API Validation
The API testing was performed using Postman targeting the `demo.evershop.io` environment.

**Endpoints Verified:**
1.  **Product Search (GraphQL):**
    * **URL:** `https://demo.evershop.io/api/graphql`
    * **Operation:** Querying `products(filters: [{key: "keyword", value: "stainless steel thermos"}])`
    * **Result:** Verified `productId`, `sku`, and `price` fields.

2.  **Add to Cart (REST):**
    * **URL:** `https://demo.evershop.io/api/cart/{cart_uuid}/items`
    * **Method:** POST
    * **Payload:** `{"sku":"THERMO-005-BLK","qty":2}`
    * **Result:** 200 OK, Item added successfully.

---

## Conclusion
The application is stable for the primary "Happy Path" user journey. However, the **Search Module requires significant development work** to meet the client's requirements regarding fuzzy search, localization (Banglish), and UI feedback (keyword highlighting). The Voice Search feature is currently missing entirely.

**Tested By:** Oynndrila Singh Purkayestha
**Date:** 2026-01-15
EOF
