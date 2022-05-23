# Show Single Account

Show a single Account if current User has access permissions to it.

- **🌏 URL**: `/api/accounts/:pk/`
- **📋 URL Parameters**: `pk=[integer]` where `pk` is the ID of the Account in the database.
- **🛤️ Method**: `GET`
- **🔐 Auth required**: `YES`
- **🚫 Permissions required** : User is at least one of the following in relation to the Account requested:
  - Owner `OO`
  - Admin `AA`
  - Viewer `VV`

## 📥 Responses

### ❌ Error Response
- **❓ Condition**: *If Account does not exist with `id` of provided `pk` parameter.*
  - **🔢 Code**: `404 NOT FOUND`
  - **✉ Content Example**:
    ```json
    {
      "error": true,
      "message": "Account doesn't exist."
    }
    ```

- **❓ Condition**: If Account exists but Authorized User does not have required
permissions.
  - **🔢 Code**: `403 FORBIDDEN`
  - **✉ Content Example**:
    ```json
    {
      "error": true,
      "message": "You do not have permission to perform this action."
    }
    ```


### ✅ Success Response
- **❓ Condition**: If Account exists and Authorized User has required permissions.
  - **🔢 Code**: `200 OK`
  - **✉ Content Example**:
    ```json
    {
      "error": false,
      "message": "The account was found.",
      "data": {
        "id": 345,
        "name": "Super Account",
        "enterprise": false,
        "url": "http://testserver/api/accounts/345/"
      }
    }
    ```

## ⚠️ Notes
There are security issues:
- This view allows existing users to test for existence of accounts that exist but that they do not have access to.
- Account IDs are sequential so an authorized user can count all the Accounts on the system.
