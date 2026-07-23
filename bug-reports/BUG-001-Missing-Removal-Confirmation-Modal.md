# 🐛 Defect Report: [BUG-001] Missing Confirmation Modal on Dependent Removal Workflow

**Defect ID:** `BUG-001`  
**Module:** Dependents Management (`ADD&REMOVE DEPENDANTS`)  
**Test Case Reference:** `CP-007-DEP-003`  
**Severity:** Medium (S3 - Major UX Safeguard Violation)  
**Priority:** High (P2 - Required for Operational Acceptance)  
**Target Platform:** Flutter Web & Mobile (Android/iOS)  
**Status:** Open / Escalated to Frontend & Middleware Teams  

---

## 📌 Defect Overview
When a Principal Member initiates a dependent removal request on the **Dependants** view, tapping the **Submit** button immediately dispatches the request payload to the SHA Admin system (`Pending Decision`). 

The expected UI confirmation pop-up modal (*"Are you sure you want to remove this dependant?"*) is completely bypassed. This creates a critical UX hazard where users can accidentally submit irreversible removal applications without an explicit confirmation step.

---

## 🔄 Reproduction Steps
1. Log in to the application as an active Principal Member.
2. Navigate to **My Profile** $ --> **Dependants** tab.
3. Locate an active dependent record and tap the **Remove** button.
4. Select a mandatory reason (e.g., *Death Certificate*) and upload a valid supporting document (`Death_Certificate.pdf`).
5. Tap **Submit**.

---

## 🎯 Expected vs. Actual Results

| Test Parameter | Expected Behavior | Actual Behavior |
| :--- | :--- | :--- |
| **User Confirmation Guardrail** | A confirmation modal pop-up appears asking *"Are you sure you want to remove this dependant?"* with **Confirm** and **Cancel** options. | No modal pop-up is rendered. The submission triggers immediately upon clicking **Submit**. |
| **Backend Payload Route** | Request payload routes to SHA Admin Console marked as `Pending Decision`. | Request payload routes correctly to SHA Admin Console as `Pending Decision`. |
| **Error Logging** | System processes request cleanly without API console exceptions. | System occasionally logs an unhandled exception: `Beneficiary not found with idType: 3 and idNumber: 359041719`. |

---

## 💻 API Payload Evidence

```json
// Dispatched Endpoint: POST /api/v1/dependents/remove-request
{
  "principal_id": "P-8839201",
  "dependent_id": "359041719",
  "id_type": 3,
  "removal_reason": "Death Certificate",
  "document_reference": "DOC-99201-DC.pdf"
}

// Console Error Response (Under Mismatched ID Type Conditions):
{
  "status": "fail",
  "code": 404,
  "message": "Beneficiary not found with idType: 3 and idNumber: 359041719"
}

🛠️ Root Cause Hypothesis & Recommendation
Frontend (Flutter): The submit action handler directly invokes the API provider method without wrapping the call inside a showDialog() modal widget.

Backend API Middleware: The backend enum mapping requires explicit translation for idType: 3 to ensure queries against the beneficiary database match the expected primary key structure.