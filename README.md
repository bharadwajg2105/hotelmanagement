# CNYKRA Hotel Housekeeping

A focused **hotel housekeeping operations system** designed to help managers and housekeeping staff manage daily room cleaning, assignments, checklists, inspections, and room readiness from a single dashboard.

Built as part of the **CNYKRA Technologies Full Stack Developer — Developer Assessment**.

## 1. Problem

Hotel housekeeping is a highly operational and labor-intensive workflow. Teams need to coordinate room assignments, cleaning progress, inspections, and room readiness throughout the day.

When this coordination depends on manual boards, calls, radios, or scattered communication, managers can lose visibility into which rooms are being cleaned, who is responsible, and which rooms are ready for inspection.

### Research & Evidence

I chose housekeeping after looking at current hospitality operations research rather than treating it as a generic hotel-management problem.

The **American Hotel & Lodging Association (AHLA)** reported in its 2024 survey that **76% of surveyed hotels were experiencing staffing shortages**, with **housekeeping ranked as the most critical hiring need by 50% of respondents**. This makes efficient coordination of existing housekeeping staff particularly relevant.

Research from **HotelTechReport**, based on feedback from **1,725 hoteliers across 77 countries**, identifies room assignment, room-status tracking, task management, mobile housekeeping workflows, and room inspections as important capabilities in modern housekeeping software.

Its 2026 hotel technology research also found that **44% of surveyed hotels consider housekeeping and operations tools a top integration priority**, indicating that housekeeping is an active area of hotel technology investment.

Based on this research, I narrowed the assessment problem to:

 **How can a hotel give managers and housekeepers a simple shared workflow for assigning, cleaning, checking, and approving rooms without requiring a full property-management system?**

CNYKRA Hotel Housekeeping is my focused implementation of that workflow.

## Solution

CNYKRA provides a simple digital workflow for managing the complete housekeeping cycle:

**Dirty → Assigned → Cleaning → Ready → Inspected**

Managers can manage the daily room schedule, assign housekeepers, and inspect completed rooms. Housekeepers get a dedicated workspace to manage their assigned rooms and cleaning checklists.

The product intentionally focuses on **one specific hospitality problem: housekeeping operations**.

## Key Features

- 🔐 JWT-based authentication
- 👥 Role-based Manager & Housekeeper access
- 🏨 Daily room schedule management
- 👤 Assign rooms to housekeepers
- 🧹 Start and track cleaning tasks
- ✅ Room-specific cleaning checklists
- ⏱️ Cleaning start/completion tracking
- 🚨 Normal, High & VIP priorities
- 🔍 Manager inspection and approval workflow
- 📝 Inspection feedback and touch-up workflow
- 📋 Recent housekeeping activity feed
- 🔎 Room search and floor filtering
- 📱 Responsive UI
- 🔔 User feedback through notifications and status updates

## Tech Stack

**Frontend**
- React 18
- React Router
- Axios
- Vite

**Backend**
- Node.js
- Express.js
- REST APIs
- JWT
- bcryptjs

**Database**
- MongoDB
- Mongoose
- MongoDB Memory Server fallback

## Application Workflow

```text
Manager
   │
   ├── Add / Manage Rooms
   │
   ├── Assign Housekeeper
   │
   ▼
Assigned
   │
   ▼
Housekeeper starts cleaning
   │
   ▼
Cleaning
   │
   ├── Complete checklist
   │
   ▼
Ready for Inspection
   │
   ▼
Manager Inspection
   │
   ├── Approved ──────► Inspected / Guest Ready
   │
   └── Rejected ──────► Touch-up Required
```

## Project Structure

```text
Cnykra-Hotel-Housekeeping/
│
├── client/
│   └── src/
│       ├── components/
│       ├── context/
│       ├── pages/
│       └── utils/
│
├── server/
│   ├── config/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── seed.js
│   └── server.js
│
├── package.json
└── README.md
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/LalitMohanAgnihotri/Cnykra-Hotel-Housekeeping.git

cd Cnykra-Hotel-Housekeeping
```

### 2. Install dependencies

The project provides a convenient installation script:

```bash
npm run install-all
```

Or install manually:

```bash
npm install

cd client
npm install
cd ..
```

### 3. Configure environment variables

Create a `.env` file in the project root:

```env
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
```

The application will attempt to connect to the configured MongoDB instance. If the connection is unavailable, it automatically falls back to **MongoDB Memory Server** for local development.

> Never commit real credentials or `.env` files to GitHub.

### 4. Start the application

Run both frontend and backend together:

```bash
npm run dev
```

Or start them separately:

```bash
npm run server
```

```bash
npm run client
```

Frontend:

```text
http://localhost:5173
```

Backend:

```text
http://localhost:5000
```

Health check:

```text
http://localhost:5000/api/health
```

## Demo Accounts

The project includes seeded demo accounts for evaluation.

### Manager

```text
Email:    manager@cnykra.com
Password: manager123
```

### Housekeepers

```text
Pooja Sharma
Email:    pooja@cnykra.com
Password: clean123

Rohan Verma
Email:    rohan@cnykra.com
Password: clean123

Sunita Patel
Email:    sunita@cnykra.com
Password: clean123
```

The login screen also provides one-click demo login for the seeded accounts.

## API Overview

```text
POST   /api/auth/login
GET    /api/auth/me

GET    /api/rooms
POST   /api/rooms
PUT    /api/rooms/:id/assign
PUT    /api/rooms/:id/start
PUT    /api/rooms/:id/checklist/:idx
PUT    /api/rooms/:id/ready
PUT    /api/rooms/:id/inspect
DELETE /api/rooms/:id

GET    /api/users
GET    /api/users/activity

GET    /api/health
```

## Author

**Mayank Bhardwaj**

Full Stack Developer

[GitHub](https://github.com/bharadwajg2105)

---

### Assessment

**CNYKRA Technologies — Full Stack Developer Assessment**

The project was intentionally kept focused on the housekeeping workflow rather than expanding into a complete hotel management platform.
