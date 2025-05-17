# User Management System

A fullstack user management system with:
- **Angular 17** frontend (SPA)
- **Node.js/Express** backend (REST API)
- **MySQL** database (hosted on Railway or your own server)
- Features: User registration, login, email verification, password reset, admin management of accounts, employees, departments, requests, and workflows.

---

## Table of Contents

- [Project Structure](#project-structure)
- [Features](#features)
- [Setup Instructions](#setup-instructions)
  - [1. Clone the Repository](#1-clone-the-repository)
  - [2. Backend Setup](#2-backend-setup)
  - [3. Frontend Setup](#3-frontend-setup)
- [Deployment](#deployment)
  - [Deploying Frontend to Render](#deploying-frontend-to-render)
  - [Deploying Backend to Railway](#deploying-backend-to-railway)
- [Environment Variables & Config](#environment-variables--config)
- [Troubleshooting](#troubleshooting)
- [License](#license)

---

## Project Structure

```
user-management/
│
├── backend/                # Node.js/Express API
│   ├── accounts/           # Account controllers, models, services
│   ├── departments/        # Department controllers, models, services
│   ├── employees/          # Employee controllers, models, services
│   ├── requests/           # Request controllers, models, services
│   ├── workflows/          # Workflow controllers, models, services
│   ├── _middleware/        # Middleware (e.g., error handler)
│   ├── _helpers/           # Helpers (e.g., Swagger docs)
│   ├── config.json         # Backend config (DB, JWT, SMTP)
│   ├── server.js           # Main Express app
│   └── package.json
│
├── frontend/               # Angular 17 SPA
│   ├── src/
│   │   ├── app/
│   │   │   ├── account/    # Login, register, email verification, etc.
│   │   │   ├── admin/      # Admin features (accounts, employees, etc.)
│   │   │   ├── profile/    # User profile
│   │   │   ├── _services/  # Angular services for API calls
│   │   │   ├── _models/    # TypeScript models
│   │   │   └── ...
│   │   ├── environments/   # Angular environment configs
│   │   └── ...
│   ├── angular.json
│   ├── package.json
│   └── ...
│
├── README.md
└── ...
```

---

## Features

### **Frontend (Angular)**
- User registration, login, email verification, password reset
- Admin dashboard: manage accounts, employees, departments, requests, workflows
- Responsive UI

### **Backend (Node.js/Express)**
- RESTful API for all resources
- JWT authentication & authorization
- Email sending for verification and password reset
- Swagger API docs (`/api-docs`)

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd user-management
```

---

### 2. Backend Setup

```bash
cd backend
npm install
```

- Copy `config.json` or use environment variables to configure:
  - Database connection (MySQL)
  - JWT secret
  - SMTP settings for email
- **Create the required MySQL tables** as described in the backend code or migrations. (See the models in `/backend/*/*.model.js` for structure.)

**Start the backend:**
```bash
npm start
```
- The API will run on `http://localhost:4000` (or the port set in `server.js`).

---

### 3. Frontend Setup

```bash
cd ../frontend
npm install
```

- Edit `src/environments/environment.prod.ts` and `environment.ts` to set the correct `apiUrl` for your backend.

**Start the frontend (dev mode):**
```bash
npm start
```
- The app will run on `http://localhost:4200`.

---

## Deployment

### Deploying Frontend to Render

- Create a **Static Site** on Render.
- **Root Directory:** `frontend`
- **Build Command:** `npm install && npm run build`
- **Publish Directory:** `dist/angular-signup-verification-boilerplate/browser`
- Ensure `_redirects` file is present in the publish directory with:
  ```
  /*    /index.html   200
  ```

### Deploying Backend to Railway

- Create a **Node.js** service on Railway (or your preferred host).
- Set environment variables for DB connection, JWT secret, etc.
- Deploy the backend code.

---

## Environment Variables & Config

**Backend:**
- `DB_HOST` - MySQL host
- `DB_PORT` - MySQL port
- `DB_USER` - MySQL user
- `DB_PASSWORD` - MySQL password
- `DB_NAME` - MySQL database name
- `JWT_SECRET` - Secret for signing JWT tokens
- `EMAIL_FROM` - Email address for outgoing mail
- `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS` - SMTP server settings

**Frontend:**
- Edit `src/environments/environment.prod.ts`:
  ```typescript
  export const environment = {
    production: true,
    apiUrl: 'https://your-backend-url'
  };
  ```

---

## Troubleshooting

- **404 Not Found on Render:**  
  Ensure the publish directory is set to the correct `browser` folder and `_redirects` file is present.
- **CORS errors:**  
  Make sure the backend CORS config allows your frontend's deployed URL.
- **Database errors:**  
  Ensure your tables are created and your DB credentials are correct.
- **Cannot connect to DB:**  
  Double-check DB credentials and Railway variables.

---

## License

MIT

---

**For more details, see the code comments and Swagger API docs at `/api-docs` on your backend.**
