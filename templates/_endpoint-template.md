# feature-name

A brief explanation of the API feature or endpoint.

- **🌏 URL**: `/`
- **📋 URL Parameters**: (the url parameter to be passed, such as `id=a-32`)
- **🛤️ Method**: `POST`, `GET`, `PUT`, `DELETE`, `PATCH` (Remove that not used)
- **🔐 Auth required**: `NO`, `YES` (Remove that not used or type the authentication type, such as `Bearer-Token`)
- **🚫 Permissions required**: (type any permission that required to access this endpoint, such as `owner`, `editor`, `viewer`, etc.)

> Take a note of these examples to choose which attribute to be the root of tree list:
	> - [Two different condition but the response code is same.](../examples/user/get.md)
	> - [Two different condition and response code.](../examples/accounts/post.md)

## 📤 Request(s)

- **📋 Data Constraint**
  - variable: `data specification` (such as `required`, `min=6 chars`, etc.)

- **✉ Data Example**
  > type the data example in json or xml format
  ```json
  {
    "username": "iloveauth@example.com",
    "password": "abcd1234"
  }
  ```

## 📥 Response(s)

> Type the error response first, so you won't miss any error handling.

### ❌ Error Response(s)
- **❓ Condition**: *The condition that produces this error response.*
  - **🔢 Code**: `400 BAD REQUEST` (HTTP response status code with its short name.)
  - **✉ Content Example**:
    > type the data example in json or xml format
    ```json
    {
      "error": true,
      "message": "Unable to login with provided credentials."
    }
    ```

### ✅ Success Response(s)
- **❓ Condition**: *The condition that produces this success response.*
  - **🔢 Code**: `200 OK` (HTTP response status code with its short name.)
  - **✉ Content Example**:
    > type the data example in json or xml format
    ```json
    {
      "error": false,
      "message": "You've logged in successfully.",
      "data": {
        "token": "93144b288eb1fdccbe46d6fc0f241a51766ecd3d"
      }
    }
    ```

## ⚠️ Note(s)
If there is any different concern, you can type it here. See these examples:
- [The note in general](../examples/accounts/pk/get.md)
- [The note contains a specific rule for endpoint.](../examples/accounts/pk/put.md)
