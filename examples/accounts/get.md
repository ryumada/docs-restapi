# Show Accessible Accounts

Show all Accounts the active User can access and with what permission level.
Includes their own Account if they have one.

- **🌏 URL**: `/api/accounts/`
- **🛤️ Method**: `GET`
- **🔐 Auth required**: `YES`
- **🚫 Permissions required**: None

## 📥 Responses
### ✅ Success Responses
- **🔢 Code**: `200 OK`
- **✉ Content Examples**:
  - **❓ Condition**: *User can not see any Accounts.*
    ```json
    {
      "error": false,
      "message": "No User found.",
      "data": []
    }
    ```
  - **❓ Condition** : *User can see one or more Accounts.*
    > In this example, the User can see three Accounts as AccountAdmin `AA`, Viewer `VV`, and Owner `OO` - in that order.
    ```json
    {
      "error": false,
      "message": "There are 3 users found.",
      "data": [
        {
          "account": {
            "id": 123,
            "name": "Lots of Admins Project",
            "enterprise": false,
            "url": "http://testserver/api/accounts/123/"
          },
          "permission": "AA"
        },
        {
          "account": {
            "id": 234,
            "name": "Feel free to View this",
            "enterprise": false,
            "url": "http://testserver/api/accounts/234/"
          },
          "permission": "VV"
        },
        {
          "account": {
            "id": 345,
            "name": "Mr Owner Project",
            "enterprise": false,
            "url": "http://testserver/api/accounts/345/"
          },
          "permission": "OO"
        }
      ]
    }
    ```
