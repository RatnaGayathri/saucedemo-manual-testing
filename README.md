# 🛒 SauceDemo – Manual QA Test Suite

A comprehensive manual testing project for [SauceDemo](https://www.saucedemo.com) — a sample e-commerce web application by Sauce Labs, used for QA practice and portfolio demonstration.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Test Execution Summary](#test-execution-summary)
- [Modules Covered](#modules-covered)
- [Bug Summary](#bug-summary)
- [Key Findings](#key-findings)
- [Test Cases](#test-cases)
- [Bug Reports](#bug-reports)
- [Tools Used](#tools-used)

---

## Overview

| Field | Details |
|---|---|
| **Application** | SauceDemo — sample e-commerce web app by Sauce Labs |
| **URL** | [https://www.saucedemo.com](https://www.saucedemo.com) |
| **Testing Type** | Functional Black-Box Testing · Manual Execution |
| **Primary User** | `standard_user` / `secret_sauce` |
| **Other Users** | `locked_out_user` (lockout testing) · `problem_user` (exploratory — intentionally broken) |
| **Browser** | Google Chrome (latest stable version) |
| **Total Test Cases** | 65 across 5 modules |
| **Bugs Found** | 13 bugs — 5 Critical, 2 High, 3 Medium, 3 Low |

---

## Test Execution Summary

| Module | Total TCs | Pass | Fail | Pass Rate | Bugs Found | Highest Severity |
|---|:---:|:---:|:---:|:---:|:---:|:---:|
| Login | 9 | 8 | 1 | 88.9% | 1 | 🔴 Critical |
| Inventory | 20 | 18 | 2 | 90.0% | 3 | 🟠 Medium, Low |
| Your Cart | 11 | 10 | 1 | 90.9% | 1 | 🟠 High |
| Checkout | 16 | 15 | 1 | 93.8% | 2 | 🟠 High |
| Special User Scenarios | 8 | 1 | 7 | 12.5% | 7 | 🔴 Critical |
| **TOTAL** | **65** | **51** | **13** | **78%%** | **13** | |

---

## Modules Covered

### 🔐 Login
- Valid credentials (Login button & Enter key)
- Invalid username / invalid password combinations
- Blank username / blank password / both blank
- Browser back/forward session handling
- Logout functionality

### 📦 Inventory
- Product list display and data completeness
- Add to cart / Remove from cart
- Cart icon count updates
- Sorting: Name (A-Z), Name (Z-A), Price (Low–High), Price (High–Low)
- Product detail page navigation and data accuracy
- Product image consistency
- Back to Products navigation
- Cart data consistency (inventory vs cart page)

### 🛒 Your Cart
- Cart navigation and product display
- Single and multiple product scenarios
- Remove product from cart
- Continue Shopping navigation (with and without products)
- Checkout navigation (with and without products)
- Product detail page access from cart
- Cart icon updates from product details page

### 💳 Checkout
- Checkout information page — valid and invalid inputs (blank first name, last name, postal code)
- Cancel button behaviour (Your Information page & Overview page)
- Checkout overview — pricing validation (item total, tax, final total)
- Product removal from product details page during checkout
- Checkout completion and order confirmation
- Cart state after order completion
- Empty cart checkout validation

### 🔍 Exploratory Testing – Special User Scenarios
- `locked_out_user` — lockout message verification
- `problem_user` — product image accuracy, product detail page navigation, sorting, add to cart, remove from cart, cart state consistency, checkout last name field

---

## Bug Summary

| Bug ID | Module | Severity | Priority | Status | Title |
|---|---|:---:|:---:|:---:|---|
| Bug-001 | Login | 🔴 Critical | High | Open | User can access Inventory page via browser forward button after logout |
| Bug-002 | Inventory | 🟢 Low | Low | Open | Sorting dropdown arrow is not clickable |
| Bug-003 | Inventory | 🟢 Low | Low | Open | Selected sorting option resets to default after navigating back from product details |
| Bug-004 | Your Cart | 🟠 Medium | Medium | Open | User is able to checkout without adding products |
| Bug-005 | Checkout | 🟠 Medium | High | Open | User is able to complete full checkout with empty cart |
| Bug-006 | Inventory | 🟡 High | Medium | Open | Incorrect product images displayed (problem_user) |
| Bug-007 | Inventory | 🔴 Critical | High | Open | Each product navigates to incorrect product details page (problem_user) |
| Bug-008 | Inventory | 🟠 Medium | Medium | Open | Sorting functionality not working (problem_user) |
| Bug-009 | Inventory | 🔴 Critical | High | Open | Remove button is not working (problem_user) |
| Bug-010 | Inventory | 🟡 High | High | Open | Cart state not reflected on product details page (problem_user) |
| Bug-011 | Inventory | 🔴 Critical | High | Open | Only 3 products can be added to cart (problem_user) |
| Bug-012 | Checkout | 🔴 Critical | High | Open | Last Name field does not accept input (problem_user) |

---

## Key Findings

### ✅ Coverage
All core user journeys tested end-to-end: Login → Inventory → Cart → Checkout. Additional exploratory coverage for `locked_out_user` and `problem_user` goes beyond basic portfolio scope and demonstrates exploratory testing instinct.

### 🔴 Critical Bugs
5 Critical severity bugs found:
- **Bug-001** — Session not invalidated after browser back/forward navigation (Login)
- **Bug-007** — Every product navigates to the wrong product details page (problem_user)
- **Bug-009** — Remove button does not remove products from cart (problem_user)
- **Bug-011** — Only 3 out of 6 products can be added to cart (problem_user)
- **Bug-012** — Last Name field in your cart does not accept any input (problem_user)

### 🛒 Empty Cart Bug (End-to-End)
A significant defect was identified and traced end-to-end:
- **TC-C-007 / Bug-004** — Checkout button proceeds with empty cart (no validation)
- **TC-Ch-016 / Bug-005** — Full checkout flow completes successfully with no products ordered

Both bugs are linked and documented with full reproduction steps.

### 🔃 Sort Defects
Two sort-related bugs identified:
- **Bug-002** — Dropdown arrow icon is non-functional (does not open dropdown)
- **Bug-003** — Selected sort order resets to default after navigating to product detail and back

---

## Test Cases

| Sheet | Contents |
|---|---|
| Summary | Overall execution summary and key findings |
| Login | TC-L-001 to TC-L-009 |
| Inventory Page | TC-I-001 to TC-I-020 |
| Your Cart | TC-C-001 to TC-C-011 |
| Checkout | TC-Ch-001 to TC-Ch-016 |
| Special User Scenarios | TC-OU-001 to TC-OU-008 |
| Bug Reports | Bug-001 to Bug-012 |

---

## Bug Reports

All bugs are documented in the **Bug Reports** sheet of the test cases spreadsheet with:

- Bug ID and related Test Case ID
- Module and title
- Environment and pre-conditions
- Steps to reproduce
- Expected Result vs Actual Result
- Severity and Priority
- Status

---

## Tools Used

| Tool | Purpose |
|---|---|
| **Google Chrome** | Test execution browser |
| **Google Sheets** | Test case documentation and bug tracking |
| **SauceDemo** | Application under test |
| **GitHub** | Version control and portfolio |

---

> **Note:** SauceDemo is a publicly available demo application intentionally designed with defects (especially for `problem_user`) for QA practice purposes.

*Manual Testing · Functional Black-Box Testing · Exploratory Testing*
