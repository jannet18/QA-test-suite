### File 2: `bug-reports/BUG-002-BRS-Auto-Member-Validation-Exception.md`

Save this file as `bug-reports/BUG-002-BRS-Auto-Member-Validation-Exception.md`:

```markdown
# 🐛 Defect Report: [BUG-002] Registry/Beneficiary System Auto-Member Creation 400 Validation Exception

**Defect ID:** `BUG-002`  
**Module:** Patient Registration /Beneficiary System Middleware Integration (`PRBS`)  
**Test Case Reference:** `TC-BRS-01`  
**Severity:** High (S2 - Integration Handshake Failure)  
**Priority:** High (P1 - Core Sync Dependency)  
**Target Platform:** Frappe REST Backend Gateway / CR-BMS Microservice  
**Status:** Resolved in Staging / Verified by QA  

---

## 📌 Defect Overview
During initial login for clean portal users, the system attempts to auto-register the member in the Beneficiary Management System (BMS). The portal first queries `GET /v1/brs/fetch-principal-member/3/[id]`, which returns `404 Not Found` as expected. 

However, the subsequent `POST /v1/brs/create-principal-member` request initially failed with a `400 Bad Request` validation exception due to strict date format constraints on the payload serialization layer, blocking auto-member creation on the initial attempt.

---

## 🔄 Reproduction Steps (API Execution)
1. Execute `GET /v1/brs/fetch-principal-member/3/359041719` using Postman.
2. Observe `404 Not Found` response (*Member not found*).
3. Execute `POST /v1/brs/create-principal-member` with standard registration payload containing `dob` as `DD-MM-YYYY`.
4. Inspect API response.

---

## 🎯 Expected vs. Actual Results

| Layer | Expected Behavior | Actual Behavior |
| :--- | :--- | :--- |
| **Initial Query (`GET`)** | Returns `404 Not Found` for unonboarded user. | Returns `404 Not Found` (Correct). |
| **Auto-Creation (`POST`)** | Returns `200 OK` or `201 Created` and registers principal member in BMS. | Returned `400 Bad Request` with message: `Validation Exception: Invalid ISO date format`. |
| **Re-Query Verification** | Subsequent `GET` returns `200 OK` with principal record. | Member creation failed initially; required payload date adjustment before succeeding. |

---

## 💻 Technical Logs & Resolution

```json
// Initial Failed Request Payload: POST /v1/bms/create-principal-member
{
  "id_type": 1,
  "id_number": "359041719",
  "first_name": "Christian",
  "phone": "+254700000000",
  "dob": "15-08-1992" // Non-compliant format
}

// Error Response:
{
  "status": "error",
  "code": 400,
  "error_type": "ValidationException",
  "message": "Field 'dob' must follow ISO 8601 standard (YYYY-MM-DD)"
}
✅ Resolution Verification
The serialization layer in the portal API gateway was updated to sanitize and format date strings to YYYY-MM-DD before dispatching to the PR/BRS endpoint. Re-testing confirmed auto-member creation executes cleanly on the first attempt without duplicating active records.