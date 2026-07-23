# 🧪 Test Suite 03: Eligibility Testing Evaluation Wizard

**Module:** Dynamic Income & Asset Assessment Engine  
**Suite ID:** `TS-MNS`  
**Target Systems:** Flutter Multi-step Wizard & Evaluation Rule Engine  
**Traceability:** `BRD-ES-001`, `BRD-ES-002`, `BRD-ES-003`

---

## 📋 Test Scenarios

### Test Case: `CP-017-STATIC-001` – Initiate Eligible Testing Evaluation
*   **Description:** Verify banner navigation and pre-checks before opening evaluation wizard.
*   **Execution Steps:**
    1. Navigate to page containing **Means Testing** banner.
    2. Click **Get Started**.
*   **Expected Result:** If no dependents exist, system alerts user to add dependents first. Otherwise, user is navigated cleanly to **Step 1: Education Background**.
*   **Execution Status:** **PASS**

---

### Test Case: `CP-017-STATIC-003` – Form Memory & "Back" Button State
*   **Description:** Ensure user inputs are preserved when navigating backward through the wizard steps.
*   **Execution Steps:**
    1. Complete Step 1 and progress to **Step 3: Confirm Details**.
    2. Click **Back** button to return to Step 2.
*   **Expected Result:** User is returned to **Step 2: Household Characteristics**. All previously entered fields remain intact and pre-filled.
*   **Execution Status:** **PASS**