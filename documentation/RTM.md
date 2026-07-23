# 🔗 Requirements Traceability Matrix (RTM)

**Project:** Care Sphere Digital Health Portal  
**Document Version:** 1.0.0  
**Target Systems:** Flutter Frontends (Web/Mobile), Frappe Backend REST APIs, CR/BMS Middleware

---

## 🎯 Executive Traceability Summary

The Requirement Traceability Matrix (RTM) ensures bidirectional mapping between business requirements (BRDs), operational test scenarios, execution outcomes, and open defect logs.

*   **Total Business Requirements Mapped:** 18
*   **Total Associated Test Scenarios:** 276
*   **Requirements Coverage:** **100%** (All functional requirements have at least 1 corresponding test scenario)
*   **Fully Verified Requirements:** 15
*   **Conditionally Passed / Blocked Requirements:** 3 *(Blocked due to external sandbox data dependencies)*

---

## 📋 Comprehensive RTM Breakdown

| Business Requirement ID | Module / Feature Area | Business Requirement Description | Associated Test Case IDs | Test Execution Status | Linked Defect / Observation |
| :---: | :--- | :--- | :---: | :---: | :---: |
| **BRD-REG-001** | Patient Onboarding | System must support National ID self-registration with SMS OTP verification & 4-digit PIN setup. | `CP-001-REG-001` | **PASS** | None |
| **BRD-REG-002** | Patient Onboarding | System must support Passport self-registration flow for international/diplomatic users. | `CP-001-REG-002` | **UNTESTED** | Blocked on test data provision |
| **BRD-REG-003** | Authentication | System must validate user security PIN and issue authenticated JWT sessions. | `CP-001-PIN-001` | **PASS** | None |
| **BRD-PAGE-001** | Home Dashboard | Display personalized greeting with legal member name and verification badges. | `CP-004-HOME-001` | **PASS** | None |
| **BRD-PAGE-002** | Home Dashboard | Display real-time employment status indicator (e.g., *Employed*, *Self-Employed*). | `CP-004-HOME-002` | **PASS** | None |
| **BRD-PAGE-003** | Home Dashboard | Render active Insurance Cover details, including provider logo and SHA number. | `CP-004-HOME-003` | **PASS** | None |
| **BRD-DEP-001** | Dependents Management | Render complete list of registered dependents with bio-data and action controls. | `CP-007-DEP-001` | **PASS** | None |
| **BRD-DEP-002** | Dependents Management | Display modal window with full legal dependent bio-data upon selecting "View". | `CP-007-DEP-002` | **PASS** | None |
| **BRD-DEP-003** | Dependents Management | Require reason selection and supporting doc upload (e.g., Death Cert) for removal. | `CP-007-DEP-003` | **PASS** | `BUG-001` (Missing Confirmation Modal) |
| **BRD-INS-001** | Insurance Cover | Active menu highlight when navigating to the Insurance Cover module. | `CP-012-INS-001` | **PASS** | None |
| **BRD-INS-002** | Insurance Cover | Display valid status badges for PHC, SHIF, and ECCIF coverage components. | `CP-012-INS-002` | **PASS** | None |
| **BRD-INS-003** | Insurance Cover | Default view to "Contributions" tab for non-eligible/self-employed profiles. | `CP-012-INS-003` | **PASS** | None |
| **BRD-ES-001** | Means Testing | Display dynamic "Get Started" banner and check dependent status before starting. | `CP-017-STATIC-001` | **PASS** | None |
| **BRD-ES-002** | Means Testing | Support multi-step wizard step-through (Step 1 Education $\rightarrow$ Step 2 Household). | `CP-017-STATIC-002` | **PASS** | None |
| **BRD-ES-003** | Means Testing | Preserve all previously entered user input when navigating backwards via "Back" button. | `CP-017-STATIC-003` | **PASS** | None |
| **BRD-BRS-001** | CR/BMS Integration | Auto-register new members in BMS upon initial login without duplicating records. | `TC-BRS-01` | **PASS** | `BUG-002` (400 Validation Exception handling) |
| **BRD-BRS-002** | CR/BMS Integration | Real-time immediate eligibility token generation for principal and dependents. | `TC-BRS-02` | **PASS** | None |
| **BRD-ENH-001** | Enhancements | Support deferred file uploads during pre-registration flows until final submission. | `TC-PREREG-01` | **PASS** | None |