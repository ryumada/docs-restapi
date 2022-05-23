# Create User's Account

Create an Account for the authenticated User if an Account for that User does not already exist. Each User can only have one Account.

- **🌏 URL**: `/api/accounts/`
- **🛤️ Method**: `POST`
- **🔐 Auth required**: `YES`
- **🚫 Permissions required**: None

## 📤 Request
- **📋 Data constraints**
  - name: `unicode`, `max=64 chars`
    > Provide name of Account to be created.
- **✉ Data examples**
    > All fields must be sent.
    ```json
    {
      "name": "Build something project dot com"
    }
    ```

## 📥 Responses
### ❌ Error Response
- **❓ Condition**: *If Account already exists for User.*
  - **🔢 Code** : `303 SEE OTHER`
  - **🔝 Headers** : `Location: http://testserver/api/accounts/123/`
  - **✉ Content Example**:
    ```json
    {
      "error": true,
      "message": "Account already exist for {{username}}. Please try another one."
    }
    ```
- **❓ Condition**: *If fields are missed.*
  - **🔢 Code** : `400 BAD REQUEST`
  - **✉ Content Example**:
    ```json
    {
      "error": true,
      "message": "There are one or more fields missed. Please check carefully.",
      "data": {
        "name": [
            "This field is required."
        ]
      }
    }
    ```

### ✅ Success Response
- **❓ Condition**: If everything is OK and an Account didn't exist for this User.
  - **🔢 Code**: `201 CREATED`
  - **✉ Content Example**:
    ```json
    {
      "error": false,
      "message": "The account was created successfully.",
      "data": {
        "id": 123,
        "name": "Build something project dot com",
        "url": "http://testserver/api/accounts/123/"
      }
    }
    ```
