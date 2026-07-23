# 🧪 Test Suite 02: Patient & Dependents Lifecycle Management

**Module:** Beneficiary & Dependents Management  
**Suite ID:** `TS-DEP`  
**Target Systems:** Flutter Frontends & Dependent Service APIs  
**Traceability:** `BRD-DEP-001`, `BRD-DEP-002`, `BRD-DEP-003`

---

## 📋 Test Scenarios

### Test Case: `CP-007-DEP-001` – Dependents List View Validation
*   **Description:** Verify display of all registered dependents linked to a Principal Member profile.
*   **Pre-conditions:** Authenticated Principal Member with active linked dependents.
*   **Execution Steps:**
    1. Navigate to **My Profile** page.
    2. Select **Dependants** tab.
    3. Observe action buttons next to each dependent record.
*   **Expected Result:** Page displays a full list of linked dependents with legal bio-data (Name, ID, Age, Gender). Each record displays **Remove** and **View** options.
*   **Execution Status:** **PASS**


---

### Test Case: `CP-007-DEP-003` – Official Dependent Removal Flow
*   **Description:** Validate initiation of a dependent removal request requiring document evidence upload.
*   **Execution Steps:**
    1. On the **Dependants** tab, click **Remove** for a specific dependent.
    2. Select a valid removal reason (e.g., *Death Certificate*).
    3. Upload required PDF document attachment.
    4. Click **Submit**.
*   **Expected Result:** A confirmation pop-up modal (*"Are you sure you want to remove this dependant?"*) should appear. Upon confirmation, payload routes to Beneficiary Admin as `Pending Decision`.
*   **Actual Observation:** Request submits successfully and reaches backend as `Pending Decision`, but **no confirmation pop-up is displayed**.
*   **Execution Status:** **PASS (With Observation)**
*   **Linked Defect:** `BUG-001`