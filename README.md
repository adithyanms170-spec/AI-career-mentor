# AI Personal Career Mentor

An intelligent academic & industry career mentoring web application designed to guide computer science undergraduates and early-career developers. 

Built with **React.js (Vite)**, **Node.js (Express.js)**, **Firebase Firestore & Authentication**, and the **Google Gemini API**.

---

## 🚀 Key Features

1. **AI Career Path Recommendations**: Synthesizes student academic profile, coursework, and personal projects to recommend top-tier industry trajectories with skill gaps and salary benchmarks.
2. **Personalized Learning Roadmaps**: Generates custom multi-phase curriculums with milestone completion toggles and vetted resource links.
3. **Resume ATS & Impact Auditor**: Ingests resume PDFs, calculates an objective ATS pass benchmark, and rewrites bullet points using the Google XYZ formula (`Accomplished [X] as measured by [Y], by doing [Z]`).
4. **Mock Interview Simulator**: Progressive conversational technical drills powered by Gemini with instant rubrics on strengths and growth areas.
5. **Security & Data Isolation**: Centralized Firebase Admin JWT verification (`verifyIdToken`), zero client-side AI key exposure, and student-scoped Firestore multi-tenancy.

---

## 📁 Project Architecture

```
ai-career-mentor/
├── client/                     # React + Vite Frontend Single Page Application
│   ├── src/
│   │   ├── config/             # Firebase Client SDK initialization
│   │   ├── context/            # AuthContext (Firebase Auth + Offline Dev Bypass)
│   │   ├── services/           # Axios apiClient with Bearer token interceptor
│   │   ├── styles/             # Design system tokens (Cyber dark + Glassmorphism)
│   │   ├── components/layout/  # Sidebar, Navbar, AppLayout, ProtectedRoute
│   │   └── views/              # Dashboard, Career, Roadmap, Resume, Interview, Profile, Login
├── server/                     # Node.js + Express.js API Gateway
│   ├── src/
│   │   ├── config/             # Firebase Admin & Gemini 2.5 SDK singletons
│   │   ├── middlewares/        # verifyIdToken Auth, Rate Limiters, Multer, Error Handler
│   │   ├── routes/             # Auth, Users, Career, Roadmaps, Resumes, Interviews
│   │   └── utils/              # PDF text parser, Standard API response envelope
│   ├── server.js               # Express HTTP listener
│   └── .env.example            # Environment variables template
├── docs/                       # System architecture & database schema documentation
│   └── SYSTEM_DESIGN.md
└── package.json
```

---

## 🛠️ Quick Start

### 1. Start the Backend API Server
```bash
cd server
npm install
npm run dev
```
The server will boot on `http://localhost:5000`. You can inspect health status at:
`http://localhost:5000/api/v1/health`

### 2. Start the Frontend Client
In a separate terminal:
```bash
cd client
npm install
npm run dev
```
The client will start on `http://localhost:5173`.

### 3. Evaluation Mode
If you haven't yet wired up your Firebase project credentials or Gemini API key, you can test the full end-to-end interface immediately:
- The backend defaults to `USE_MOCK_AI=true` with safe unauthenticated dev fallbacks.
- The login view includes a 1-click **"Launch Demo Student Workspace"** button pre-populated with student credentials, allowing instant demonstration of all features.

---

## 🔒 Environment Configuration

### Server (`server/.env`)
```ini
PORT=5000
NODE_ENV=development
CLIENT_URL=http://localhost:5173
USE_MOCK_AI=true
GEMINI_API_KEY=your_gemini_api_key_here
GEMINI_MODEL=gemini-2.5-flash
# FIREBASE_PROJECT_ID=...
# FIREBASE_CLIENT_EMAIL=...
# FIREBASE_PRIVATE_KEY=...
```

### Client (`client/.env`)
```ini
VITE_API_BASE_URL=http://localhost:5000/api/v1
VITE_FIREBASE_API_KEY=your_api_key
VITE_FIREBASE_AUTH_DOMAIN=your-app.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your-project-id
```
