# 🧪 Experiment 10 — REST API with Node.js, Express.js & MongoDB

> Build and test CRUD REST APIs using Node.js, Express.js, and MongoDB — tested via Postman.

---

## 🎯 Objective

- Build REST APIs using **Node.js** and **Express.js**
- Connect backend with **MongoDB** database using **Mongoose**
- Perform **Create, Read, Update, Delete** (CRUD) operations
- Test APIs using **Postman**
- Understand backend **routing** and **controllers**

---

## 💻 Tech Stack

| Component | Technology |
|-----------|------------|
| Runtime | Node.js |
| Framework | Express.js |
| Database | MongoDB (local) |
| ODM | Mongoose |
| CORS | cors |
| Dev Server | Nodemon |
| API Testing | Postman |

---

## ⚙️ Installation

```bash
mkdir experiment10
cd experiment10
npm init -y
npm install express mongoose cors nodemon
```

---

## 📁 Project Structure
experiment10/
├── server.js
├── models/
│   └── Student.js
├── routes/
│   └── studentRoutes.js
└── package.json

---

## 🧱 Backend Implementation

### 📄 `server.js`

```js
const express = require("express");
const mongoose = require("mongoose");
const cors = require("cors");

const app = express();
app.use(express.json());
app.use(cors());

mongoose.connect("mongodb://127.0.0.1:27017/collegeDB")
  .then(() => console.log("Database Connected"))
  .catch(err => console.log(err));

const studentRoutes = require("./routes/studentRoutes");
app.use("/api/students", studentRoutes);

app.listen(5000, () => {
  console.log("Server running on port 5000");
});
```

### 📄 `models/Student.js`

```js
const mongoose = require("mongoose");

const studentSchema = new mongoose.Schema({
  name: String,
  email: String,
  course: String
});

module.exports = mongoose.model("Student", studentSchema);
```

### 📄 `routes/studentRoutes.js`

```js
const express = require("express");
const router = express.Router();
const Student = require("../models/Student");

// CREATE
router.post("/", async (req, res) => {
  const data = await Student.create(req.body);
  res.json(data);
});

// READ ALL
router.get("/", async (req, res) => {
  const data = await Student.find();
  res.json(data);
});

// READ SINGLE
router.get("/:id", async (req, res) => {
  const data = await Student.findById(req.params.id);
  res.json(data);
});

// UPDATE
router.put("/:id", async (req, res) => {
  const data = await Student.findByIdAndUpdate(req.params.id, req.body, { new: true });
  res.json(data);
});

// DELETE
router.delete("/:id", async (req, res) => {
  await Student.findByIdAndDelete(req.params.id);
  res.json({ message: "Record Deleted Successfully" });
});

module.exports = router;
```

---

## ▶️ Run the Project

```bash
nodemon server.js
```

---

## 🌐 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/students` | Create a new record |
| `GET` | `/api/students` | Fetch all records |
| `GET` | `/api/students/:id` | Fetch record by ID |
| `PUT` | `/api/students/:id` | Update record by ID |
| `DELETE` | `/api/students/:id` | Delete record by ID |

---

## 🧪 API Testing (Postman)

### ➕ Create Record
POST /api/students
```json
{
  "name": "Rahul",
  "email": "rahul@gmail.com",
  "course": "BCA"
}
```

### 📋 Get All Records
GET /api/students

### 🔍 Get Single Record
GET /api/students/:id

### ✏️ Update Record
PUT /api/students/:id
```json
{
  "course": "MCA"
}
```

### ❌ Delete Record
DELETE /api/students/:id

---

## 📸 Required Screenshots

1. MongoDB Connected Message
2. Create Record API Success
3. Read All Records Output
4. Update Record Success
5. Delete Record Success
6. Database Collection View

---

## 📘 Summary

- **Node.js + Express.js** used as backend framework
- **MongoDB** stores student records
- **CRUD operations** implemented via REST APIs
- **Postman** used for end-to-end API testing
