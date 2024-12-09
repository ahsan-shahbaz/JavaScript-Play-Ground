# JWT API Manager with Token Refresh

A simple and reusable JavaScript utility to manage API requests with JSON Web Token (JWT) authentication, including automatic token refreshing. This project is designed to be modular and adaptable to various applications.

---

## Features

- **Centralized API Endpoint Management**: Easily manage API endpoints in a single configuration file.
- **JWT Token Management**: Handle access tokens and refresh tokens securely using `localStorage`.
- **Automatic Token Refresh**: Automatically refresh JWT tokens before expiration.
- **Standard CRUD Support**: Provides helper methods for common HTTP requests (GET, POST, PUT, DELETE).
- **Error Handling**: Handles token expiration, retry logic, and redirects to login on authentication failure.

---

## File Structure

### 1. `ApiConstants.js`

Defines all API endpoints and base URLs for your application. Includes dynamic endpoints for resource-specific operations.

#### Example Usage
```javascript
// Importing API Constants
import API from './ApiConstants.js';

// Accessing Endpoints
const loginUrl = API.Constants.URL.LOGIN;
```
### 2. `ApiManager.js`

Handles all API interactions. Includes token management, automatic retries for failed requests due to token expiration, and reusable methods for HTTP operations.

#### Example Usage
```javascript
// Importing ApiManager
import ApiManager from './ApiManager.js';

// Making a GET Request
const tasks = await ApiManager.Get(API.Constants.URL.TASKS);

// Making a POST Request
const newTask = await ApiManager.Post(API.Constants.URL.CREATE_TASK, { title: "New Task" });
```

## Installation

1. Clone or download the repository.
2. Ensure you have the required dependencies (e.g., `jQuery`).
3. Include the necessary files in your project.

### Include via HTML
```html
<script src="path/to/jquery.min.js"></script>
<script src="path/to/ApiConstants.js"></script>
<script src="path/to/ApiManager.js"></script>
```

### Include via Module (ES6)
```javascript
import API from './ApiConstants.js';
import ApiManager from './ApiManager.js';
```

### Configuration
### Update the Base URL
Edit the `BASE_URL` in `ApiConstants.js` to point to your backend server:

```javascript
API.Constants.BASE_URL = "http://your-backend-server/api/v1";
```

### API Constants

### Defined Endpoints
The `ApiConstants.js` file contains the following endpoints:
  - ### Authentication
    - `LOGIN`: `POST /auth/login`
    - `REFRESH_TOKEN`: `POST /auth/token/refresh`
    - `LOGOUT`: (Optional)
  - ### Tasks
    - `TASKS`: `GET /tasks`
    - `CREATE_TASK`: `POST /tasks`
    - `EDIT_TASK`: `PUT /tasks/:taskId`
    - `DELETE_TASK`: `DELETE /tasks/:taskId`

### Example: Dynamic Endpoints
```javascript
const editTaskUrl = API.Constants.URL.EDIT_TASK(taskId);
```

### API Manager
### Token Management
The `ApiManager.js` file relies on `localStorage` for storing JWT tokens. It includes methods for setting, retrieving, and refreshing tokens.
### Example: Access Token Management
```javascript
TokenManager.setAccessToken("your-access-token");
const token = TokenManager.getAccessToken();
```
### CRUD Operations
`Get(url, params)`
Send a GET request.
```javascript
const tasks = await ApiManager.Get(API.Constants.URL.TASKS);
```

`Post(url, data)`
Send a POST request with data.
```javascript
const newTask = await ApiManager.Post(API.Constants.URL.CREATE_TASK, { title: "Task Title" });
```

`Put(url, data)`
Send a PUT request with data.
```javascript
const updatedTask = await ApiManager.Put(API.Constants.URL.EDIT_TASK(taskId), { title: "Updated Task Title" });
```

`Delete(url)`
Send a DELETE request.
```javascript
await ApiManager.Delete(API.Constants.URL.DELETE_TASK(taskId));
```
### Automatic Token Refresh
The `ApiManager` automatically refreshes tokens if they are about to expire.


### Error Handling
### Token Expiration
  - If the token is expired, `ApiManager` attempts to refresh it automatically.
  - If refreshing fails, the user is redirected to the login page.
### Debugging
All errors are logged to the console for easy debugging:
```javascript
console.error("Error:", error);
```

### License
This project is licensed under the MIT License. Feel free to use, modify, and distribute it for your projects.

### Contributions
Contributions are welcome! If you find any issues or have feature suggestions, please open an issue or submit a pull request.

### Acknowledgments
This utility was inspired by the need for a simple yet powerful JWT management solution for client-side applications. Built with `JavaScript` and `jQuery`.

### Key Highlights of the README:

1. **Generic Description**: Removed any project-specific metadata to make the tool adaptable for other applications.
2. **Structured Sections**: Organized the file into clear sections for easier navigation.
3. **Comprehensive Documentation**: Covered all major features and usage scenarios, ensuring even a first-time user can implement it.
4. **Open-Source Focus**: Highlighted licensing and contribution guidelines to align with open-source principles.



