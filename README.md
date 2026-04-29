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
| Inventory | 21 | 18 | 3 | 85.7% | 3 | 🟡 Low |
| Your Cart | 11 | 10 | 1 | 90.9% | 2 | 🟠 Medium |
| Checkout | 16 | 15 | 1 | 93.8% | 2 | 🟠 Medium |
| Special User Scenarios | 8 | 1 | 7 | 12.5% | 7 | 🔴 Critical |
| **TOTAL** | **65** | **52** | **13** | **80%** | **13** | |

---

## Modules Covered

### 🔐 Login
- Valid credentials (Login button & Enter key)
- Invalid username / invalid password combinations
- Blank username / blank password / both blank
- Browser back/forward session handling
- Logout functionality

### 📦 Inventory
- Product list display and data accuracy
- Add/remove products from inventory page and product detail page
- Cart badge count updates
- All four sorting options (Name A-Z, Z-A, Price low-high, high-low)
- Sort order persistence after navigation
- Sorting dropdown arrow functionality
- Product data consistency between inventory and cart

### 🛒 Your Cart
- Cart navigation and product display (single and multiple products)
- Remove product from cart
- Continue Shopping navigation (with and without products)
- Checkout navigation (with and without products)
- Cart icon updates via product detail page
- Product detail page access from cart

### 💳 Checkout
- Your Information form — valid submission and required field validation
- Cancel button behaviour
- Overview page — price, tax, and total accuracy
- Product detail navigation from overview
- Checkout completion flow
- Empty cart checkout behaviour

### 👤 Special User Scenarios
- `locked_out_user` — lockout error message validation
- `problem_user` — product images, product navigation, sorting, add/remove to cart, cart state, checkout form

---

## Bug Summary

| Bug ID | TC | Module | Description | Severity | Priority |
|---|---|---|---|:---:|:---:|
| Bug-001 | TC-L-008 | Login | User can access Inventory page via browser Forward button after navigating Back — session not invalidated | 🔴 Critical | High |
| Bug-002 | TC-I-002 | Inventory | Last product name appears incorrect — `"Test.allTheThings() T-Shirt (Red)"` | 🟡 Low | Low |
| Bug-003 | TC-I-012 | Inventory | Sorting dropdown arrow icon is not clickable | 🟡 Low | Low |
| Bug-004 | TC-I-013 | Inventory | Selected sort order resets to default after navigating to product detail and back | 🟡 Low | Low |
| Bug-005 | TC-C-007 | Your Cart | Checkout proceeds with empty cart — no validation applied | 🟠 Medium | Medium |
| Bug-006 | TC-Ch-017 | Checkout | Full checkout flow completes with zero products — order confirmed with empty cart | 🟠 Medium | High |
| Bug-007 | TC-OU-002 | Inventory (problem_user) | Incorrect product images displayed on inventory and product detail pages | 🟠 High | Medium |
| Bug-008 | TC-OU-003 | Inventory (problem_user) | Clicking a product opens incorrect product details page — mismatched name, image, description, price | 🔴 Critical | High |
| Bug-009 | TC-OU-004 | Inventory (problem_user) | Sorting functionality does not work — product order does not change | 🟠 Medium | Medium |
| Bug-010 | TC-OU-005 | Inventory (problem_user) | Remove button does not function — product cannot be removed from cart | 🔴 Critical | High |
| Bug-011 | TC-OU-006 | Inventory (problem_user) | Product details page does not reflect cart state — shows Add to Cart when item already in cart | 🟠 High | High |
| Bug-012 | TC-OU-007 | Inventory (problem_user) | Not all products can be added to cart — some Add to Cart buttons are unresponsive | 🔴 Critical | High |
| Bug-013 | TC-OU-008 | Checkout (problem_user) | Last Name field does not accept input on checkout form — user cannot proceed | 🔴 Critical | High |

> Full reproduction steps, expected results, and actual results for each bug are documented in the **Bug Reports** sheet of the test cases file.

---

## Key Findings

**1. Session not invalidated on browser back (Bug-001)**
After logging in, pressing the browser Back button and then Forward returns the user to the Inventory page without requiring re-login. This is a security concern that would be a high-priority fix in a production application.

**2. Empty cart checkout completes end-to-end (Bug-005, Bug-006)**
The checkout flow can be initiated with an empty cart and completed all the way through to the order confirmation page. No validation exists at any stage to prevent this. A real order is effectively placed with zero items.

**3. problem_user has 7 critical and high defects**
Exploratory testing with the `problem_user` account uncovered 7 defects including broken product navigation (wrong detail pages), non-functional remove button, unresponsive Add to Cart buttons, incorrect product images, and an unresponsive Last Name field on the checkout form. All documented with full reproduction steps.

**4. Sort order not persisted after navigation (Bug-004)**
Selecting a sort option and navigating to a product detail page causes the sort to silently reset to default (Name A-Z) when returning to inventory. This is a usability bug that would frustrate users browsing a large catalogue.

---

## Test Cases

📄 **[Test-Cases.xlsx](./Test-Cases.xlsx)**

The workbook contains the following sheets:

| Sheet | Contents |
|---|---|
| `Summary` | Dashboard — module stats, pass/fail counts, bug summary, key findings |
| `Login` | 9 test cases covering login functionality |
| `Inventory` | 21 test cases covering product listing, sorting, add/remove, navigation |
| `Your Cart` | 11 test cases covering cart management and navigation |
| `Checkout` | 16 test cases covering the full checkout flow |
| `Exploratory Testing – Special U` | 8 test cases for locked_out_user and problem_user |
| `Bug Reports` | 13 bugs with full reproduction steps, expected/actual results, severity, and priority |

---

## Bug Reports

All bugs are documented in the **Bug Reports** sheet of [Test-Cases.xlsx](./Test-Cases.xlsx) with the following information for each:

- Bug ID and related TC ID
- Module and title
- Environment
- Preconditions
- Steps to reproduce
- Expected result
- Actual result
- Severity and priority
- Status

---

## Tools Used

| Tool | Purpose |
|---|---|
| Google Chrome | Test execution browser |
| Google Sheets / Excel | Test case management and bug tracking |
| GitHub | Version control and portfolio hosting |
| automation(playwright) *(planned)* | Automation for selected high-priority test cases |

---

## 🤖 Automation Candidates

The following test cases are identified for automation(playwright) (Page Object Model pattern):

- `TC-L-001`, `TC-L-002` — Login with valid credentials
- `TC-L-003`, `TC-L-004` — Invalid credentials error message validation
- `TC-L-005`, `TC-L-006`, `TC-L-007` — Blank field validation
- `TC-I-003`, `TC-I-004` — Add to cart and cart badge count
- `TC-Ch-003`, `TC-Ch-004`, `TC-Ch-005` — Checkout form required field validation

> Automation scripts coming soon in a separate `/automation` directory.

---

*Created as part of a QA portfolio to demonstrate manual test case design, defect identification, exploratory testing, and structured documentation skills.*
