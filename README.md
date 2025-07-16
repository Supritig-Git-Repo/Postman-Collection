This repository contains a Postman collection for testing a booking API, covering token generation, creating bookings, updating bookings, and retrieving booking details.

Included Requests
1. **Create Token**
Generates an auth token to be used in subsequent requests.

**Test Validations:**
- Status code is `200`
- Token is set in the environment
- Response follows the defined JSON schema
- Token field exists in the response

2. **Create Booking**
Creates a new booking using dynamic data (with environment variables).

**Test Validations:**
- Booking ID is generated and saved
- Response matches the expected JSON schema
- All booking details match the request
- Booking ID is a number and greater than 100
- Content-Type header is correct (`application/json; charset=utf-8`)
- Response time is under 2000ms
- Request body fields (e.g., firstname, lastname) are **not null**
- Name fields must **not contain special characters**

---

### 3. **Update Booking**
Updates the booking details created in the previous step.

**Test Validations:**
- If `checkin < checkout`:
  - Status code is `200`
  - Response values match the updated request body
  - Environment variables are updated with new values
- If `checkin >= checkout`:
  - Status code is `422` (Unprocessable Entity)
- Name fields must **not contain special characters**
- Null validation on all key fields in request body

---

4. **Get Booking**
Retrieves the booking details using the booking ID.

**Test Validations:**
- Response matches the expected JSON schema
- Returned booking details match the stored environment variables
- Correct Content-Type in response header
- Response time under 1500ms

---

**How to Use**

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/your-repo.git
