# ⚛️ TeamFlow Frontend: React.js SPA

This is the frontend client for **TeamFlow**, an interactive, single-page Employee Management application. Built with **React.js (v16.13.1)** and styled using **Bootstrap 4**, it consumes the REST endpoints exposed by the Spring Boot backend to manage workforce directory details with a responsive interface.

---

## 🛠️ Tech Stack & Key Modules

-   **React.js 16.13.1:** Employs component-oriented architecture (class components) with modular states.
-   **React Router DOM 5.2.0:** Manages dynamic client-side SPA routing (`BrowserRouter`, `Switch`, `Route`).
-   **Axios:** Executes high-performance Promise-based HTTP calls, managing request payloads and response states asynchronously.
-   **Bootstrap 4.5.0:** Integrates clean grid layouts, styling configurations, buttons, and form inputs.
-   **cross-env:** Seamlessly sets system environment variables across platforms (Windows, macOS, Linux).

---

## 📂 Source Code structure

```directory
src/
├── components/
│   ├── HeaderComponent.js         # Top navigation header bar
│   ├── FooterComponent.jsx        # Footer layout with copyright notes
│   ├── ListEmployeeComponent.jsx  # Main view showing list of employees in a table
│   ├── CreateEmployeeComponent.jsx# Dual-purpose form to Add or Update employees
│   ├── ViewEmployeeComponent.jsx  # Card layout view for individual employee details
│   └── UpdateEmployeeComponent.jsx# Deprecated update view (consolidated into CreateEmployeeComponent)
│
├── services/
│   └── EmployeeService.js         # Unified client layer mapping API CRUD actions with Axios
│
├── App.js                         # Router setup and page routing mapping
└── index.js                       # Render root configuration
```

---

## 🏗️ Technical Highlights

### 1. Dual-Purpose Components (`CreateEmployeeComponent.jsx`)
Rather than creating separate views, the component detects if it is in "create" or "edit" mode using route parameters:
-   `/add-employee/_add` ➡️ Starts with empty fields for creation.
-   `/add-employee/:id` ➡️ Triggers a lifecycle hook `componentDidMount()` to fetch existing employee data via `EmployeeService.getEmployeeById(id)` and populates form fields for updates.

### 2. Service Encapsulation (`EmployeeService.js`)
API interactions are isolated from UI components. This layer manages base REST URLs (`http://localhost:8080/api/v1/employees`) and exposes reusable methods:
```javascript
getEmployees()
createEmployee(employee)
getEmployeeById(employeeId)
updateEmployee(employee, employeeId)
deleteEmployee(employeeId)
```

### 3. Node v17+ Compatibility
To support modern Node runtimes (like Node.js v18/v20/v24), we configure `cross-env` with `NODE_OPTIONS=--openssl-legacy-provider` in the execution scripts. This instructs Node to bypass OpenSSL 3.x strict cryptographic defaults, which are incompatible with older Webpack compiler setups.

---

## ⚙️ Quick Start

### 1. Prerequisites
- **Node.js** (v18+)
- **npm** (v9+)

### 2. Environment Setup
Create a `.env` or set configurations in `src/services/EmployeeService.js` to target the Spring Boot endpoint. By default:
```javascript
const EMPLOYEE_API_BASE_URL = "http://localhost:8080/api/v1/employees";
```

### 3. Build and Run Commands
- **Install Dependencies:**
  ```bash
  npm install
  ```
- **Run the local Development Server:**
  ```bash
  npm start
  ```
  The server starts at `http://localhost:3000`.

- **Compile and Build for Production:**
  ```bash
  npm run build
  ```
  Compiles production-ready bundle output to the `build/` directory.

---

## 🛡️ Role-Based Key Competencies (Frontend Focus)

*   **SPA Routing:** Structuring nested routing systems with clean parameters and clean navigation lifecycle management.
*   **State Management:** State segregation using local state variables, prop extraction, and event handling hooks.
*   **API Integration:** Asynchronous communication handling with API wrapper models.
