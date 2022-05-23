# Login

Used to collect a Token for a registered User.

- **🌏 URL**: `/api/login/`
- **🛤️ Method**: `POST`
- **🔐 Auth required**: `NO`

## 📤 Request

- **📋 Data Constraint**
  - username: `valid email address`, `required`
  - password: `plain text`, `required`, `min=6 characters`

- **✉ Data Example**
  ```json
  {
    "username": "iloveauth@example.com",
    "password": "abcd1234"
  }
  ```

## 📥 Responses

### ❌ Error Response
- **❓ Condition**: *If `username` and `password` combination is wrong.*
  - **🔢 Code**: `400 BAD REQUEST`
  - **✉ Content Example**:
    ```json
    {
      "error": true,
      "message": "Unable to login with provided credentials."
    }
    ```

### ✅ Success Response
- **🔢 Code**: `200 OK`
- **✉ Content Example**:
  ```json
  {
    "error": false,
    "message": "You've logged in successfully.",
    "data": {
      "token": "93144b288eb1fdccbe46d6fc0f241a51766ecd3d"
    }
  }
  ```
