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

---

## Installation

1. Clone or download the repository.
2. Ensure you have the required dependencies (e.g., `jQuery`).
3. Include the necessary files in your project.

### Include via HTML
```html
<script src="path/to/jquery.min.js"></script>
<script src="path/to/ApiConstants.js"></script>
<script src="path/to/ApiManager.js"></script>

### Include via Module (ES6)

import API from './ApiConstants.js';
import ApiManager from './ApiManager.js';



### Configuration

Update the Base URL
Edit the BASE_URL in ApiConstants.js to point to your backend server:

```javascript
API.Constants.BASE_URL = "http://your-backend-server/api/v1";






















You can now copy and paste the content into your `.md` file. Let me know if further modifications are needed!





