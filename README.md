# QuickAI ⚡

AI-Powered Content Generation Platform — built with the PERN stack and integrated with OpenAI, Cloudinary, and Clerk.

🌐 **Live Demo:** [quickai-server-kappa.vercel.app](https://quickai-server-kappa.vercel.app)

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [API Endpoints](#api-endpoints)
- [Deployment](#deployment)
- [License](#license)

---

## Overview

QuickAI is a full-stack AI SaaS platform that lets users generate images, write articles, create blog titles, remove image backgrounds, remove objects from images, and get AI-powered resume reviews — all in one place.

Authentication is handled by Clerk, media management by Cloudinary, and the database runs on PostgreSQL (Neon).

---

## Features

- **Image Generation** — Text-to-image using OpenAI DALL-E
- **Background Removal** — Automatic AI-based background removal
- **Object Removal** — Clean up images by removing unwanted objects
- **Article Writing** — AI-assisted long-form content generation
- **Blog Title Generator** — Generate SEO-friendly titles from a topic
- **Resume Review** — Upload a PDF resume and get AI feedback, scoring, and gap analysis
- **Community Feed** — Browse and share creations with other users
- **User Dashboard** — Central hub for all tools and history
- **Clerk Authentication** — Secure sign-up, login, and session management
- **Responsive UI** — Works across desktop and mobile

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 19, Vite, Tailwind CSS |
| Backend | Node.js, Express 5 |
| Database | PostgreSQL (Neon) |
| AI | OpenAI API (DALL-E, GPT) |
| Auth | Clerk |
| Media | Cloudinary |
| File Uploads | Multer |
| PDF Parsing | pdf-parse |
| HTTP Client | Axios |
| Routing | React Router DOM |
| Notifications | React Hot Toast |
| Markdown | React Markdown |
| Deployment | Vercel |

---

# Project Structure

```text
QuickAI/
│
├── client/                           # React Frontend (Vite)
│   │
│   ├── public/                       # Public static files
│   │
│   ├── src/                          # Frontend source code
│   │   │
│   │   ├── assets/                   # Images, icons, and static resources
│   │   │
│   │   ├── components/               # Reusable UI components
│   │   │   ├── AITools.jsx
│   │   │   ├── CreationItem.jsx
│   │   │   ├── Footer.jsx
│   │   │   ├── Hero.jsx
│   │   │   ├── Navbar.jsx
│   │   │   ├── Plan.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   └── Testimonial.jsx
│   │   │
│   │   ├── pages/                    # Route-level application pages
│   │   │   ├── BlogTitles.jsx
│   │   │   ├── Community.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   ├── GenerateImages.jsx
│   │   │   ├── Home.jsx
│   │   │   ├── Layout.jsx
│   │   │   ├── RemoveBackground.jsx
│   │   │   ├── RemoveObject.jsx
│   │   │   ├── ReviewResume.jsx
│   │   │   └── WriteArticle.jsx
│   │   │
│   │   ├── App.jsx                   # Root application component
│   │   └── main.jsx                  # Frontend entry point
│   │
│   └── package.json                  # Frontend dependencies
│
├── server/                           # Express Backend
│   │
│   ├── configs/                      # Configuration files
│   │   ├── cloudinary.js             # Cloudinary integration setup
│   │   ├── db.js                     # PostgreSQL database connection
│   │   └── multer.js                 # File upload configuration
│   │
│   ├── controllers/                  # Business logic controllers
│   │   ├── aiController.js           # AI tool functionalities
│   │   └── userController.js         # User management operations
│   │
│   ├── middlewares/                  # Custom middleware functions
│   │   └── auth.js                   # Clerk authentication middleware
│   │
│   ├── routes/                       # API route definitions
│   │   ├── aiRoutes.js
│   │   └── userRoutes.js
│   │
│   ├── server.js                     # Backend application entry point
│   └── package.json                  # Backend dependencies
│
└── README.md                         # Project documentation
```

## Folder Description

### `client/`

Contains the React frontend built with Vite. It manages the user interface, routing, and interaction with backend APIs.

### `assets/`

Stores static resources such as images, icons, logos, and other media files.

### `components/`

Contains reusable UI components that are shared across multiple pages, improving maintainability and code reusability.

### `pages/`

Contains route-level components representing different features of the application, including image generation, article writing, resume review, and community pages.

### `server/`

Contains the Express.js backend responsible for handling API requests, authentication, AI processing, database operations, and file uploads.

### `configs/`

Stores configuration files for third-party services and application setup, including Cloudinary, PostgreSQL, and Multer.

### `controllers/`

Implements the core business logic for AI-powered features and user-related operations.

### `middlewares/`

Contains middleware functions used for authentication, authorization, request validation, and security.

### `routes/`

Defines API endpoints and maps incoming requests to their corresponding controller functions.

### `server.js`

The main backend entry point that initializes the Express server, middleware, and API routes.

---

## Getting Started

### Prerequisites

- Node.js v18+
- npm v8+
- PostgreSQL database ([Neon](https://neon.tech) recommended)
- [OpenAI](https://platform.openai.com/) API account
- [Cloudinary](https://cloudinary.com/) account
- [Clerk](https://clerk.com/) account

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/Swastikraj599/QuickAI.git
cd QuickAI
```

**2. Install client dependencies**

```bash
cd client
npm install
```

**3. Install server dependencies**

```bash
cd ../server
npm install
```

**4. Configure environment variables** (see section below)

**5. Start development servers**

```bash
# Terminal 1 — Backend
cd server
npm run server

# Terminal 2 — Frontend
cd client
npm run dev
```

Frontend runs at `http://localhost:5173`
Backend runs at `http://localhost:5000`

---

## Environment Variables

### Client — `client/.env`

```env
VITE_CLERK_PUBLISHABLE_KEY=pk_test_your_key
VITE_API_BASE_URL=http://localhost:5000
```

### Server — `server/.env`

```env
PORT=5000
DATABASE_URL=your_neon_postgres_connection_string
OPENAI_API_KEY=sk-your_openai_key
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
CLERK_SECRET_KEY=sk_test_your_clerk_secret
```

> ⚠️ Never commit `.env` files. Both are already covered by `.gitignore`.

---

## API Endpoints

### AI Routes — `/api/ai`

| Method | Endpoint | Description |
|---|---|---|
| POST | `/generate-image` | Generate image from text prompt |
| POST | `/remove-background` | Remove background from uploaded image |
| POST | `/remove-object` | Remove object from uploaded image |
| POST | `/write-article` | Generate article from topic |
| POST | `/generate-titles` | Generate blog titles from topic |
| POST | `/review-resume` | Analyse uploaded PDF resume |

### User Routes — `/api/users`

| Method | Endpoint | Description |
|---|---|---|
| GET | `/profile` | Get current user profile |
| POST | `/creations` | Save a creation |
| GET | `/creations` | Get user's saved creations |
| GET | `/community` | Get all community creations |

---

## Deployment

Frontend and backend are both deployed on **Vercel**.

For backend deployment, set all server environment variables in your Vercel project settings under **Environment Variables**.

For the database, use [Neon](https://neon.tech) — free tier is sufficient for development and small-scale production.

---

## Author

**Swastik Raj**
[GitHub](https://github.com/Swastikraj599) · [LinkedIn](https://linkedin.com/in/swastik-raj-128056204)

---

## License

Distributed under the MIT License. See `LICENSE` for details.
