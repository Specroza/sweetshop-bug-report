# SweetShop Web Application – Manual QA Case Study

A manual software testing case study performed on the SweetShop web application to identify functional defects, usability issues, validation gaps, navigation problems, and account/session-related issues.

The goal was not just to verify whether individual features worked, but to test how the application behaved in realistic user flows and edge cases.

## Application Under Test

**Live Application:**  
https://sweetshop.netlify.app/

## Test Objective

The assessment required a comprehensive functional and usability review of the application, with all identified issues documented in a structured bug report.

My testing focused on:

- Functional behaviour
- Input validation
- Checkout and order processing
- Authentication and session handling
- Basket behaviour
- Order history
- Navigation
- Responsive and mobile behaviour
- Usability
- Accessibility-related issues
- Error handling
- Data consistency

## Testing Summary

| Area | Result |
|---|---|
| Defects reported | **27** |
| Critical | **11** |
| High | **4** |
| Medium | **6** |
| Low | **6** |
| Desktop tested | Windows 11 + Google Chrome |
| Mobile tested | Pixel 9 emulation |
| Testing type | Manual Functional + Usability Testing |

> Severity and priority were assigned based on the impact of each issue on functionality, user experience, data integrity, and the ability of a user to complete a core flow.

## Key Findings

The testing uncovered several high-impact problems that could affect real users and business operations.

### Checkout & Payment Validation

The checkout flow accepted invalid or arbitrary values across important billing and payment fields. CVV validation also allowed negative numbers and values outside the expected length.

The application could therefore accept invalid payment information without blocking the order.

### Incorrect Order Total Calculation

The Standard Shipping option produced incorrect totals.

For some whole-number subtotals, the shipping fee appeared to be concatenated with the subtotal instead of being mathematically added. For fractional subtotals, the total could become `NaN`.

More importantly, the application still allowed the order to be completed even when the displayed total was invalid.

### Account & Session Issues

Several issues were found around authentication and session management.

A second account could be logged in without properly ending the first session, and account-specific data was not isolated correctly.

This resulted in:

- Basket contents appearing across different accounts
- Support chat history being visible to another account
- Inconsistent account information after page refresh
- No visible logout option

These were treated as high-risk findings because they go beyond simple UI defects and affect user data isolation.

### Navigation & Mobile Compatibility

Navigation behaviour was inconsistent between different parts of the application.

The About page could return a Page Not Found response from the Basket page, while navigation links failed completely when the application was tested using a Pixel 9 mobile viewport.

### Order History

Completed orders did not appear correctly in the logged-in user's order history.

Sorting the order history table also caused row data to become incorrectly ordered.

### Usability & Accessibility

Additional usability issues included:

- No useful placeholder text in checkout fields
- Support chat could only be closed using the X icon
- Login text had poor contrast against the background
- No custom 404 page
- Header behaviour while scrolling was inconsistent
- Product image failure for Wham Bars
- Quantity adjustment issues in the basket
- Stale checkout instructions remaining after order completion

## Defect Highlights

Some of the highest-impact defects identified during testing were:

| Bug ID | Finding | Severity | Priority |
|---|---|---|---|
| BG-001 | Empty basket can be submitted as a completed order | Critical | P1 |
| BG-002 | No validation on payment and billing fields | Critical | P1 |
| BG-003 | CVV accepts negative numbers and invalid lengths | Critical | P1 |
| BG-004 | Standard shipping produces incorrect / `NaN` totals | Critical | P1 |
| BG-005 | Invalid `NaN` order total can still be submitted | Critical | P1 |
| BG-009 | Basket contents leak between user accounts | Critical | P1 |
| BG-010 | Support chat history leaks between accounts | Critical | P1 |
| BG-011 | Account information becomes inconsistent after refresh | Critical | P1 |
| BG-026 | Navigation breaks on mobile viewport | Critical | P1 |

The complete report contains all **27 documented defects**, including reproduction steps, expected behaviour, actual behaviour, environment details, severity, priority, and evidence references. :contentReference[oaicite:2]{index=2} :contentReference[oaicite:3]{index=3} :contentReference[oaicite:4]{index=4}

## Testing Approach

I approached the application from an end-user perspective and deliberately tested both normal flows and invalid/edge-case scenarios.

The testing included:

1. Exploring the application and its main user journeys
2. Verifying expected behaviour of core features
3. Testing invalid and unexpected inputs
4. Checking checkout calculations and order submission
5. Testing authentication and session behaviour
6. Switching between user accounts to verify data isolation
7. Refreshing pages to check state persistence
8. Testing navigation across different pages
9. Testing the application in a mobile viewport
10. Recording reproducible defects with clear steps and expected vs actual results

## Environment

**Desktop**

- OS: Windows 11
- Browser: Google Chrome
- Browser Version: 153.0.8010.53
- Architecture: 64-bit

**Mobile**

- Google Chrome DevTools mobile emulation
- Device profile: Pixel 9

## Deliverables

### Bug Report

The complete bug report contains all identified issues with:

- Bug ID
- Environment
- Severity
- Priority
- Defect title
- Steps to reproduce
- Expected result
- Actual result
- Evidence

**Report:** `SweetShop - Bug Report.pdf`

## Skills Demonstrated

This case study demonstrates practical experience in:

- Manual Software Testing
- Functional Testing
- Usability Testing
- Regression-oriented thinking
- Boundary Value Analysis
- Negative Testing
- Input Validation Testing
- Checkout Testing
- Authentication Testing
- Session Testing
- Data Isolation Testing
- Responsive / Mobile Testing
- Defect Identification
- Severity & Priority Classification
- Structured Bug Reporting
- Reproduction of Real-world User Flows

## What I Learned

This case study reinforced an important part of QA: a feature working on the happy path does not necessarily mean the product is working correctly.

The most serious issues were not visual defects. They appeared when the application was pushed with invalid input, unusual navigation, account switching, page refreshes, and unexpected checkout states.

That is the mindset I try to bring to software testing: **don't just test whether something works; test how and when it fails.**

## Project

**Application:** SweetShop  
**Testing Type:** Manual QA  
**Focus:** Functional, Usability, Validation, Authentication, Session, Navigation & Mobile Testing  
**Defects Identified:** 27
