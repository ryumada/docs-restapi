# Update Current User

Allow the Authenticated User to update their details.

- **🌏 URL**: `/api/user/`
- **🛤️ Method**: `PUT`
- **🔐 Auth required**: `YES`
- **🚫 Permissions required**: None

## 📤 Request
- **📋 Header constraints**
  - UAPP: `1 to 8 chars`
    > The application used to update the User's information can be sent in the header. Values passed in the `UAPP` header only pass basic checks for validity:
    > -  If 0 characters, or not provided, ignore.
    > - If 1 to 8 characters, save.
    > - If longer than 8 characters, ignore.
- **📋 Data constraints**
  - first_name: `1 to 30 chars`
  - last_name: `1 to 30 chars`
    > Note that `id` and `email` are currently read only fields.
- **✉ Data examples**
  > Partial data is allowed.
  - **Just first name**
    ```json
    {
      "first_name": "John"
    }
    ```
  - Empty data can be PUT to erase the name, in this case from the iOS application version 1.2:
    
    `UAPP: ios1_2`  
    ```json
    {
      "last_name": ""
    }
    ```

## 📥 Responses

### ❌ Error Response
- **❓ Condition**: *If provided data is invalid, e.g. a name field is too long.*
- **🔢 Code**: `400 BAD REQUEST`
- **✉ Content Example**:
  ```json
  {
    "error": true,
    "message": "There are one or more invalid fields.",
    "data": {
      "first_name": [
        "This field is required."
      ],
      "email": [
        "The email is invalid"
      ]
    }
  }
  ```

### ✅ Success Responses
- **❓ Condition**: *Data provided is valid and User is Authenticated.*
- **🔢 Code**: `200 OK`
- **✉ Content Example**: *Response will reflect back the updated information. A User with `id` of '1234' sets their name, passing `UAPP` header of 'ios1_2'.*
  ```json
  {
    "error": false,
    "message": "The User has been updated successfully.",
    "data": {
      "id": 1234,
      "first_name": "Joe",
      "last_name": "Bloggs",
      "email": "joe25@example.com",
      "uapp": "ios1_2"
    }
  }
  ```

## ⚠️ Notes
- Endpoint will ignore irrelevant and read-only data such as parameters that don't exist, or fields that are not editable like `id` or `email`.
- Similar to the `GET` endpoint for the User, if the User does not have a UserInfo instance, then one will be created for them.
