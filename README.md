# Experiment 10: CRUD Operations on Database using Node.js + Express.js

This repository contains the backend implementation for **Experiment 10**, demonstrating how to perform CRUD Operations (Create, Read, Update, Delete) on a database using Node.js, Express.js, and MongoDB.

## 🚀 Features

*   **Node.js and Express.js** used as the robust backend framework.
*   **MongoDB** database integration using Mongoose for reliable and flexible data storage.
*   **CRUD operations** fully formulated through a standardized REST API structure.
*   **Postman** heavily utilized for robust endpoint testing.

## 💻 Tech Stack

*   **Backend:** Node.js, Express.js
*   **Database:** MongoDB, Mongoose
*   **Tools:** Postman, nodemon

## 📸 API Screenshots & Verification

Here are the tested endpoints captured from our Postman implementation:

### 1. Database Connection OK
![MongoDB Connection Output](./screenshots/connection-ok.png)

### 2. Create Record (POST)
Endpoint: `POST /api/students`
![Create Record API Success](./screenshots/post-api.png)

### 3. Read All Records (GET)
Endpoint: `GET /api/students`
![Read All Records Output](./screenshots/get-api.png)

### 4. Read Single Record (GET)
Endpoint: `GET /api/students/:id`
![Read Single Record Output](./screenshots/get-single.png)

### 5. Update Record (PUT)
Endpoint: `PUT /api/students/:id`
![Update Record Success](./screenshots/update-api.png)

### 6. Delete Record (DELETE)
Endpoint: `DELETE /api/students/:id`
![Delete Record Success](./screenshots/delete-api.png)

## ⚙️ Installation & Run Guide

**1. Install Dependencies**
```bash
pnpm install
```

**2. Start Application**
Make sure your MongoDB server is running locally on port `27017` (`mongodb://127.0.0.1:27017/collegeDB`), then start the development server:
```bash
pnpm nodemon server.js
```
*Server runs on port 5000 (http://localhost:5000)*
