# Show Current User

Get the details of the currently Authenticated User along with basic
subscription information.

- **🌏 URL**: `/api/user/`
- **🛤️ Method**: `GET`
- **🔐 Auth required**: `YES`
- **🚫 Permissions required**: None

## 📥 Responses
## ✅ Success Response
- **🔢 Code**: `200 OK`
- **✉ Content Examples**:
  - **❓ Condition**: *For a User with ID 1234 on the local database where that User has saved an email address and name information.*
    ```json
    {
      "error": false,
      "message": "User data fetched successfully."
      "data": {
        "id": 1234,
        "first_name": "Joe",
        "last_name": "Bloggs",
        "email": "joe25@example.com"
      }
    }
    ```
  - **❓ Condition**: *For a user with ID 4321 on the local database but no details have been set yet.*
    ```json
    {
      "error": false,
      "message": "User data fetched successfully.",
      "data": {
        "id": 4321,
        "first_name": "",
        "last_name": "",
        "email": ""
      }
    }
    ```

## ⚠️ Notes
- If the User does not have a `UserInfo` instance when requested then one will be created for them.
