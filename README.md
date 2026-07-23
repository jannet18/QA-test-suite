# 🎯 Web Application Quality Assurance Portfolio
This repository showcases my end-to-end testing methodologies, test documentation standards, and test automation capabilities. 

As a QA Engineer with a software engineering background, I specialize in manual exploratory testing, technical API validation, and writing robust, maintainable automated test suites.

---

## 🛠️ Tech Stack & QA Toolkit
* **Manual Testing & Design:** Boundary Value Analysis, Equivalence Partitioning, Figma UI Parity Testing, Postman (API Testing)
* **Test Tracking & Management:** Markdown Test Matrices, Requirement Traceability Matrices (RTM)
* **CI/CD & Version Control:** Git, GitHub Actions
* **Automation Framework:** JavaScript, Playwright (or Cypress), Node.js

---

## 📂 Repository Structure

* [📂 documentation/](./documentation/) — Contains the high-level **Test Plan** and audit-ready testing deliverables.
* [📂 test-cases/](./test-cases/) — Features structured manual test cases spanning positive, negative, and edge-case scenarios.
* [📂 automation/](./automation/) — End-to-end (E2E) automated regression scripts targeting critical user workflows.

---

## 🔍 Featured Project: [Patient Portal]
For this portfolio, I designed and executed a comprehensive QA strategy for a full-stack Flutter/Frappe application to validate its performance, security, and usability.

### 📝 1. Manual Testing Artifacts
* **[Test Plan (Markdown)](./documentation/Test_Plan.md):** Outlines the scope, environmental requirements, risk-based testing focus, and pass/fail criteria.
* **[Test Case Matrix](./test-suites/CARE-SPHERE-UPDATED-07.xlsx):** Over 250 written test cases spanning authentication, input boundaries, and responsive UI layout parity against design mockups.

### 🤖 2. Automation Suite
Using **Playwright**, I automated the application's core regression path to run on multiple browser engines (Chromium, Firefox, WebKit):
* Secure login with valid/invalid credentials (handling rate-limiting and error states).
* Form input validation (ensuring boundaries and special characters are handled correctly).

---

## 🐛 Sample Bug Report
*To view the complete active bug log, visit [Bug_Reports.md](./bug-reports/).*

### **BUG-001: Profile Picture Upload Fails silently on PNG files > 5MB**
* **Severity:** Medium
* **Environment:** macOS Sonoma, Chrome v121
* **Steps to Reproduce:**
  1. Navigate to the Account Settings page.
  2. Click "Upload Profile Image".
  3. Select a `.png` file sized 5.2MB.
  4. Click "Save".
* **Expected Result:** Application displays a user-friendly error toast: *"Image size must be under 5MB."*
* **Actual Result:** The modal hangs indefinitely, and the browser console logs a `500 Internal Server Error` from the upload API endpoint.