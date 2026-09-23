# 🎓 Student Dropout Analysis & Prevention System (SDAS)

A full-stack, real-time web application designed for educational institutions to monitor student performance, predict early dropout risks, and orchestrate counselor interventions.

---

## 🌟 Key Features

- **Automated Early Warning & Risk Detection:** Real-time risk triggering engine that identifies critical drops in student attendance (`< 50%`) or academic performance (`GPA < 5.0`).
- **Real-time Counselor Alerts:** Integrated **Socket.IO** notification system that pushes instantaneous alerts to assigned counselors when a student requires urgent intervention.
- **Counselor & Administrator Portals:** Role-Based Access Control (**RBAC**) ensuring counselors only access assigned students while admins retain system-wide visibility.
- **Intervention Tracking:** Structured workflow for logging, managing, and tracking student intervention histories (parent meetings, tutoring, financial aid counseling).
- **Security & Compliance Audit Logs:** Immutable event logging tracking authentication attempts, system modifications, and intervention creations.
- **Data Analytics & Visualization:** Interactive dashboard with dynamic charts, custom multi-parameter filters (GPA, attendance, region, economic status), and server-side pagination.

---

## 🛠 Tech Stack

### **Backend**
- **Runtime:** Node.js (ES Modules)
- **Framework:** Express.js (RESTful API Design & Versioning)
- **Database:** MongoDB with Mongoose ODM
- **Real-Time:** Socket.IO
- **Security:** JWT Authentication, Bcrypt password hashing, Helmet security headers, Express Rate Limiting
- **Validation:** Express-Validator

### **Frontend**
- **Library:** React (Vite build tool)
- **State & UI:** Modern Component Architecture, Dynamic Charts (Chart.js / Recharts)
- **Real-Time:** Socket.IO Client

---

## 📁 Repository Structure

```
student-dropout-system/
├── backend/                # Express.js REST API & Socket.IO server
│   ├── config/             # Environment & App configuration
│   ├── controllers/        # Request handlers
│   ├── middleware/         # Auth, Error handling & Rate limiting
│   ├── models/             # Mongoose schemas (Student, User, Intervention, AuditLog)
│   ├── routes/             # API Endpoint definitions
│   ├── services/           # Core business & risk detection logic
│   ├── socket.js           # Socket.IO event handler
│   └── seed.js             # Database seeder script
├── frontend/               # React UI Application
│   ├── src/                # Components, Pages, Hooks, Services
│   └── public/             # Static assets
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) (v18+ recommended)
- [MongoDB](https://www.mongodb.com/) (Local instance or MongoDB Atlas cluster)

### 1. Clone the Repository
```bash
git clone https://github.com/<YOUR_GITHUB_USERNAME>/student-dropout-system.git
cd student-dropout-system
```

### 2. Backend Setup
```bash
cd backend

# Install dependencies
npm install

# Configure Environment Variables
cp .env.example .env
# Edit .env and update PORT, MONGODB_URI, and JWT_SECRET as needed

# Seed Database with Sample Student Data (Optional)
npm run seed

# Start Backend Server
npm start
```
The backend server will run on `http://localhost:3000`.

### 3. Frontend Setup
```bash
cd ../frontend

# Install dependencies
npm install

# Start Development Server
npm run dev
```
The frontend application will run on `http://localhost:5173`.

---

## 🔌 API Endpoints Summary

| Method | Endpoint | Description | Auth Required |
| :--- | :--- | :--- | :---: |
| `POST` | `/api/v1/auth/login` | User authentication & JWT generation | ❌ |
| `GET` | `/api/v1/students` | Get paginated & filtered student list | ✅ |
| `GET` | `/api/v1/students/:id` | Get specific student profile | ✅ |
| `PATCH`| `/api/v1/students/:id` | Update student metrics & trigger risk check | ✅ |
| `GET` | `/api/v1/interventions`| List logged interventions | ✅ |
| `POST` | `/api/v1/interventions`| Create new student intervention | ✅ |
| `GET` | `/api/v1/notifications`| Fetch real-time notifications | ✅ |
| `GET` | `/api/v1/audit-logs` | Retrieve system audit history | ✅ (Admin) |

---

## 📝 License
This project is open source and available under the [MIT License](LICENSE).
