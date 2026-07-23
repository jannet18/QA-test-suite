# 🧪 Test Suite 01: Registration, OTP & Security PIN Setup

**Module:** Patient Onboarding & Authentication  
**Suite ID:** `TS-REG`  
**Target Systems:** Flutter Web/Mobile Frontends & Auth REST APIs  
**Traceability:** `BRD-REG-001`, `BRD-REG-002`, `BRD-REG-003`

---

## 📋 Test Scenarios

### Test Case: `CP-001-REG-001` – National ID Self-Registration Pipeline
*   **Description:** Validate end-to-end self-registration workflow using a valid unonboarded National ID.
*   **Execution Channel:** Flutter Android / iOS / Web
*   **Pre-conditions:** Test National ID must not exist in active database records.
*   **Execution Steps:**
    1. Open the application and click **Register**.
    2. Select ID Type as **National ID**.
    3. Input a valid unonboarded ID number, matching First Name, and active Phone Number.
    4. Click **Proceed**.
    5. Enter the valid 5-digit verification OTP received via SMS.
    6. Input a new 4-digit security PIN, confirm identically in **Confirm PIN**, and tap **Proceed**.
    7. Tap **Proceed to Login** on the success screen.
*   **Expected Result:** System verifies ID against external registry, validates OTP, persists the salted security PIN, and routes user to the active login screen.
*   **Execution Status:** **PASS**


---

### Test Case: `CP-001-REG-002` – Passport Self-Registration Pipeline
*   **Description:** Validate self-registration using a Passport ID for international/diplomatic users.
*   **Execution Channel:** Flutter Mobile
*   **Pre-conditions:** Passport test data provisioned in sandbox registry.
*   **Execution Steps:**
    1. Navigate to Registration screen.
    2. Select ID Type as **Passport**.
    3. Input valid Passport ID, First Name, and Phone Number.
    4. Complete OTP verification and set 4-digit PIN.
*   **Expected Result:** System verifies passport credentials against verified registries, validates OTP, and routes user to login panel.
*   **Execution Status:** **UNTESTED** *(Awaiting external test data)*
*   **Note:** Blocked pending sandbox API credentials.