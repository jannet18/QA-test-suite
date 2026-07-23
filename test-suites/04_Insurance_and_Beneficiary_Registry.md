# 🧪 Test Suite 04: Insurance Cover & Registry/Beneficiary System Integrations

**Module:** Insurance Policies & Beneficiary Registry Middleware Synchronization  
**Suite ID:** `TS-INS-BRS`  
**Target Systems:** Rest API Gateways, Beneficiary Registry Endpoints, Policy Card Widgets  
**Traceability:** `BRD-INS-002`, `BRD-BRS-001`, `BRD-BRS-002`

---

## 📋 Test Scenarios

### Test Case: `CP-012-INS-002` – Insurance Provider Card Display
*   **Description:** Verify active status rendering for Primary Health Care, Insurance, and ECCIF coverage components.
*   **Execution Steps:**
    1. Open **Insurance Cover** page.
    2. Inspect provider card details on the left.
*   **Expected Result:** Provider card displays official logo, valid Insurance Number, and active status indicators (`Valid`) for Primary Health Care, Insurance, and ECCIF.
*   **Execution Status:** **PASS**

---

### Test Case: `TC-BRS-01` – Registry-Beneficiary Integration: Automated Member Creation API
*   **Description:** Verify backend auto-registration of new portal members in the Beneficiary Regisrty system.
*   **Execution Steps (API Level):**
    1. Send `GET /v1/brs/fetch-principal-member/3/[id]` for a unonboarded user.
    2. Verify `404 Not Found` response.
    3. Execute `POST /v1/brs/create-principal-member` with user payload.
    4. Re-query `GET` endpoint.
*   **Expected Result:** POST request creates member without generating duplicate records. Re-query returns `200 OK` with full member details.
*   **Execution Status:** **PASS**
*   **Linked Defect:** `BUG-002` *(Resolved API validation parameter mapping)*