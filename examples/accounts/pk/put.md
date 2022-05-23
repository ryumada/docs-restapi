# Update Account

Update the Account of the Authenticated User if and only if they are Owner.

- **🌏 URL**: `/api/accounts/:pk/`
- **🛤️ Method**: `PUT`
- **🔐 Auth required**: `YES`
- **🚫 Permissions required**: None

## 📤 Request

- **📋 Data constraints**
  - name: `unicode`, `max=64 chars`
- **✉ Data examples**: Partial data is allowed, but there is only one field.
    ```json
    {
        "name": "Build something project dot com",
    }
    ```

### ❌ Error Response
- **❓ Condition**: *Account does not exist at URL.*
  - **🔢 Code**: `404 NOT FOUND`
  - **✉ Content Example**:
    ```json
    {
      "error": true,
      "message": "Account does not exist."
    }
    ```
- **❓ Condition**: *Authorized User is not Owner of Account at URL.*
  - **🔢 Code**: `403 FORBIDDEN`
  - **✉ Content Example**:
    ```json
    {
      "error": true,
      "message": "You're not allowed to do this."
    }
    ```

### ✅ Success Responses

- **❓ Condition**: Update can be performed either fully or partially by the Owner of the Account.
  - **🔢 Code**: `200 OK`
  - **✉ Content Example**: For the example above, when the 'name' is updated and posted to `/api/accounts/123/...`.
    ```json
    {
      "error": false,
      "message": "Account has been successfully updated.",
      "data": {
        "id": 123,
        "name": "New project name",
        "enterprise": false,
        "url": "http://testserver/api/accounts/123/"
      }
    }
    ```

## ⚠️ Notes

### Data ignored
- **❓ Condition**: Endpoint will ignore irrelevant and read-only data such as parameters that don't exist, or `id` and `enterprise` fields which are not editable.
  > E.g. if Account already exits:

- 📤 Request
  - **✉ Data examples**
    ```json
    {
        "wibble": "flobble",
        "id": 987,
        "enterprise": true
    }
    ```

- 📥 Responses
  - ✅ Success Responses
    - **🔢 Code**: `200 OK`
    - **✉ Content Example**:
      ```json
      {
          "id": 123,
          "name": "New project name",
          "enterprise": false,
          "url": "http://testserver/api/accounts/123/"
      }
      ```
