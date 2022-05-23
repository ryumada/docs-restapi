# Delete User's Account

Delete the Account of the Authenticated User if they are Owner.

- **🌏 URL**: `/api/accounts/:pk/`
- **📋 URL Parameters**: `pk=[integer]` where `pk` is the ID of the Account in the database.
- **🛤️ Method**: `DELETE`
- **🔐 Auth required**: `YES`
- **🚫 Permissions required** : User is Account Owner

## 📥 Responses

### ❌ Error Response

- **❓ Condition**: *If there was no Account available to delete.*
  - **🔢 Code**: `404 NOT FOUND`
  - **✉ Content Example**:
	```json
	{
		"error": true,
		"message": "No account with id {{pk}}."
	}
	```

- **❓ Condition**: *Authorized User is not Owner of Account at URL.*
  - **🔢 Code**: `403 FORBIDDEN`
  - **✉ Content Example**:
	```json
	{
		"error": true,
		"message": "You are not allowed to do this."
	}
	```

### ✅ Success Response

- **❓ Condition** : If the Account exists.
  - **🔢 Code**: `200 OK`
  - **✉ Content Example**:
  	```json
  	{
  		"error": false,
  		"message": "The account has been removed successfully"
  	}
  	```

## ⚠️ Notes

- Will remove memberships for this Account for all Users that had access.
