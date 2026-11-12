# अड्डा (Adda) — Room Rental & Marketplace

A full-stack MERN platform for room rentals and local marketplace listings in Nepal.

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 19, Tailwind CSS, React Router v7 |
| Auth | Clerk (OAuth, Email) |
| Backend | Node.js, Express 5 |
| Database | MongoDB (Atlas recommended) |
| File Storage | Cloudinary |
| Maps | Leaflet / React-Leaflet |

---

## Project Structure

```
/
├── backend/          # Express API server
│   ├── config/       # Cloudinary config
│   ├── middleware/   # Auth middleware (Clerk JWT)
│   ├── models/       # Mongoose schemas
│   ├── routes/       # API routes
│   └── server.js     # Entry point
├── frontend/         # React app (Create React App)
│   ├── public/       # Static HTML, favicon
│   └── src/
│       ├── components/   # Shared UI components
│       ├── context/      # Auth & Language context
│       ├── pages/        # Route pages
│       ├── services/     # Axios API client
│       └── utils/        # Utility functions
├── render.yaml       # Render.com deploy config
└── package.json      # Root monorepo scripts
```

---

## Local Development

### Prerequisites
- Node.js >= 18
- MongoDB running locally (or Atlas URI)

### Setup

```bash
# 1. Clone the repo
git clone <your-repo-url>
cd room-rental-marketplace

# 2. Set up backend environment
cp backend/.env.example backend/.env
# Edit backend/.env with your values

# 3. Set up frontend environment
cp frontend/.env.example frontend/.env
# Edit frontend/.env with your Clerk key

# 4. Install all dependencies & start dev servers
npm install
npm run dev
```

Frontend: http://localhost:3000  
Backend API: http://localhost:5000

---

## Deployment (Render.com)

### Backend (Web Service)

1. Connect your GitHub repo on [Render](https://render.com)
2. Create a **Web Service**
3. Set:
   - **Build Command:** `npm install --prefix backend`
   - **Start Command:** `npm start`
4. Add environment variables from `backend/.env.example`

### Frontend (Static Site)

1. Create a **Static Site** on Render
2. Set:
   - **Build Command:** `npm install --prefix frontend && npm run build --prefix frontend`
   - **Publish Directory:** `frontend/build`
3. Add environment variable:
   - `REACT_APP_CLERK_PUBLISHABLE_KEY` — your Clerk publishable key
   - `REACT_APP_API_URL` — your backend Render URL + `/api`

### Required Environment Variables

#### Backend
| Variable | Description |
|---|---|
| `MONGO_URI` | MongoDB Atlas connection string |
| `CLERK_SECRET_KEY` | Clerk secret key |
| `JWT_SECRET` | Random secret string |
| `CLOUDINARY_CLOUD_NAME` | Cloudinary cloud name |
| `CLOUDINARY_API_KEY` | Cloudinary API key |
| `CLOUDINARY_API_SECRET` | Cloudinary API secret |
| `ALLOWED_ORIGINS` | Frontend URL (comma-separated) |
| `FRONTEND_URL` | Frontend URL |

#### Frontend
| Variable | Description |
|---|---|
| `REACT_APP_CLERK_PUBLISHABLE_KEY` | Clerk publishable key |
| `REACT_APP_API_URL` | Backend API base URL |

---

## Features

- 🏠 Room rental listings with geo-search
- 🛒 Marketplace for buying/selling items
- 🔐 Clerk authentication (email + OAuth)
- 📸 Cloudinary image uploads
- 🗺️ Map-based location picker (Leaflet)
- 💬 In-app messaging between users
- 🌐 English / Nepali language toggle
- 🌙 Dark mode support
- 👩‍💼 Admin dashboard
