<div align="center">

  <h1>🏡 Real-Time Wanderlust</h1>
  <h3><i>Next-Gen Airbnb Style Property Listing & Booking Platform</i></h3>

  <p align="center">
    <a href="https://github.com/BinaryBlaze16/WanderLust-Air-BnB">
      <img src="https://img.shields.io/github/stars/BinaryBlaze16/WanderLust-Air-BnB?style=for-the-badge&color=FFD700&logo=github" alt="Stars" />
    </a>
    <a href="https://github.com/BinaryBlaze16/WanderLust-Air-BnB/network/members">
      <img src="https://img.shields.io/github/forks/BinaryBlaze16/WanderLust-Air-BnB?style=for-the-badge&color=00BFFF&logo=github" alt="Forks" />
    </a>
    <a href="https://github.com/BinaryBlaze16/WanderLust-Air-BnB/issues">
      <img src="https://img.shields.io/github/issues/BinaryBlaze16/WanderLust-Air-BnB?style=for-the-badge&color=FF4500&logo=github" alt="Issues" />
    </a>
    <a href="https://github.com/BinaryBlaze16/WanderLust-Air-BnB/blob/main/LICENSE">
      <img src="https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge" alt="License" />
    </a>
  </p>

  <p align="center">
    <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white"/>
    <img src="https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white"/>
    <img src="https://img.shields.io/badge/React.js-61DAFB?style=for-the-badge&logo=react&logoColor=black"/>
    <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white"/>
    <img src="https://img.shields.io/badge/Socket.io-010101?style=for-the-badge&logo=socket.io&logoColor=white"/>
    <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white"/>
    <img src="https://img.shields.io/badge/Cloudinary-3448C5?style=for-the-badge&logo=cloudinary&logoColor=white"/>
    <img src="https://img.shields.io/badge/TailwindCSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white"/>
  </p>

  <br />

  <p align="center">
    <b>Wanderlust</b> is a high-performance, full-stack property rental ecosystem built on the MERN stack. Designed to deliver an immersive Airbnb-like user experience, featuring real-time availability updates via Socket.io, Cloudinary media processing, JWT state management, geolocation tagging, and interactive review workflows.
  </p>

</div>

<hr />

## ⚡ Table of Contents

- [📌 Project Overview](#-project-overview)
- [🏗️ System Architecture & Workflow](#️-system-architecture--workflow)
- [🚀 Key Capabilities](#-key-capabilities)
- [🧩 Core Modules](#-core-modules)
- [🛠️ Tech Stack & Dependencies](#️-tech-stack--dependencies)
- [🛰️ Real-Time Socket.io Events](#️-real-time-socketio-events)
- [📡 REST API Endpoints](#-rest-api-endpoints)
- [⚙️ Environment Configuration](#️-environment-configuration)
- [📥 Quickstart Setup Guide](#-quickstart-setup-guide)
- [🛣️ Future Roadmap](#️-future-roadmap)
- [🤝 Contributing & License](#-contributing--license)

---

## 📌 Project Overview

Wanderlust bridges the gap between property hosts and travelers by providing a robust, scalable platform for discovering, listing, and rating unique accommodations globally.

### 💡 Why Wanderlust?
- **Blazing Fast UI**: Optimized React component tree coupled with responsive TailwindCSS components.
- **Real-Time Data Transmission**: Instant notification of booking status changes and live listing view updates via Socket.io event channels.
- **Cloud Media Pipeline**: Asynchronous multi-image upload pipeline powered by Cloudinary with automatic optimization & thumbnail transformations.
- **Enterprise Security**: Password hashing with Bcrypt, JWT token authorization, CORS validation, and XSS sanitization.

---

## 🏗️ System Architecture & Workflow

```text
                                +---------------------------+
                                |    Client Application     |
                                |  (React.js + Tailwind)    |
                                +-------------+-------------+
                                              |
                        +---------------------+---------------------+
                        |                                           |
                        v HTTP REST API                             v WebSocket (Socket.io)
        +-------------------------------+           +-------------------------------+
        |    Express Backend Server     |           |     Socket.io Gateway         |
        |   (Authentication & Routes)   |           |  (Real-Time Notifications)   |
        +---------------+---------------+           +---------------+---------------+
                        |                                           |
         +--------------+--------------+                            |
         |                             |                            |
         v                             v                            v
+------------------+         +-------------------+        +-------------------+
|  MongoDB Cluster |         | Cloudinary Media  |        | Active Broadcast  |
| (Database Layer) |         |  (Storage Bucket) |        |    Event Bus      |
+------------------+         +-------------------+        +-------------------+
```

---

## 🚀 Key Capabilities

| Capability | Technical Implementation | Impact |
| :--- | :--- | :--- |
| **Authentication** | JWT Tokens & HTTP-Only Cookies | Stateful, zero-latency session validation across protected routes. |
| **Listing Engine** | CRUD with Mongoose Schema & GeoJSON | Structured query execution with filterable price & location metadata. |
| **Media Pipeline** | Multer Middleware + Cloudinary SDK | Cloud image uploads with automatic compression and webp conversion. |
| **Real-Time Bus** | Socket.io Server-Side WebSockets | Live listing updates and active occupancy alerts without polling. |
| **Review Engine** | Relational Schemas & Dynamic Aggregations | Instant star score computation and user review moderation. |

---

## 🧩 Core Modules

### 👤 1. Authentication Lifecycle
```text
[ User Register / Login ] ──► [ Passwords Hashed via Bcrypt ] ──► [ JWT Signature Generated ]
                                                                             │
[ Client Authenticated ]  ◄── [ Token Saved in Auth Context ] ◄──────────────┘
```

### 🏠 2. Listing Operations Lifecycle
```text
[ Create Listing Form ] ──► [ Image Processing (Cloudinary) ] ──► [ Mongoose Document Saved ]
                                                                             │
[ Broadcast Event ]     ◄── [ Socket.io Triggers 'LISTING_NEW' ] ◄──────────┘
```

---

## 🛠️ Tech Stack & Dependencies

### **Frontend Tier**
- **React.js** (v18+) – Component-driven UI development
- **TailwindCSS** – Custom design tokens and responsive utility classes
- **React Router DOM** – Client-side dynamic routing & route guards
- **Socket.io Client** – WebSockets client engine for real-time channels
- **Lucide Icons / Heroicons** – Vector interface icons

### **Backend Tier**
- **Node.js & Express.js** – Server framework and REST API controller layer
- **MongoDB & Mongoose** – NoSQL schema modelling & ORM layer
- **Socket.io** – Bi-directional event engine
- **JSONWebToken (JWT)** – Stateless authentication mechanism
- **Cloudinary & Multer** – Multipart form handling and image storage cloud

---

## 🛰️ Real-Time Socket.io Events

| Event Name | Direction | Payload | Trigger Condition |
| :--- | :--- | :--- | :--- |
| `connection` | Client ⇄ Server | `{ socketId, userId }` | User establishes Socket connection |
| `listing:created` | Server ➔ Clients | `{ listingId, title, price }` | Host publishes a new property listing |
| `listing:updated` | Server ➔ Clients | `{ listingId, updatedFields }` | Host edits listing details or pricing |
| `review:added` | Server ➔ Clients | `{ listingId, review }` | Guest posts a new rating/review |

---

## 📡 REST API Endpoints

### 🔑 Authentication Routes
```text
POST   /api/auth/register    - Create a new user account
POST   /api/auth/login       - Authenticate user credentials & issue JWT
GET    /api/auth/me          - Retrieve authenticated user profile
POST   /api/auth/logout      - Clear session tokens
```

### 🏡 Listing Routes
```text
GET    /api/listings         - Fetch all listings (with search & category filters)
POST   /api/listings         - Create a new listing (Requires Authentication + Multer)
GET    /api/listings/:id     - Get detailed listing by ID
PUT    /api/listings/:id     - Update existing listing (Host Only)
DELETE /api/listings/:id     - Remove listing (Host Only)
```

### ⭐ Review Routes
```text
POST   /api/listings/:id/reviews  - Post rating and review
DELETE /api/listings/:id/reviews/:reviewId - Delete review (Author/Host Only)
```

---

## ⚙️ Environment Configuration

Create a `.env` file in the `server/` directory:

```env
# Server Setup
PORT=5000
NODE_ENV=development
CLIENT_URL=http://localhost:5173

# Database
MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/wanderlust?retryWrites=true&wmode=majority

# Security
JWT_SECRET=your_super_secret_jwt_key_here
JWT_EXPIRES_IN=7d

# Cloudinary Storage
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

---

## 📥 Quickstart Setup Guide

### **Prerequisites**
- **Node.js** (v18.0.0 or higher)
- **MongoDB** (Local instance or MongoDB Atlas Cloud Cluster)
- **Git**

### **1. Clone Repository**
```bash
git clone https://github.com/BinaryBlaze16/WanderLust-Air-BnB.git
cd WanderLust-Air-BnB
```

### **2. Install Backend Dependencies & Run Server**
```bash
cd server
npm install
npm run dev
```

### **3. Install Frontend Dependencies & Run Client**
```bash
cd ../client
npm install
npm run dev
```

Open your browser at `http://localhost:5173` to explore Wanderlust live!

---

## 🛣️ Future Roadmap

- [ ] **Interactive Maps**: Integrate Mapbox / Leaflet API for interactive pin navigation.
- [ ] **Payment Gateway**: Seamless booking payments via Stripe API integration.
- [ ] **AI Property Recommendations**: Personalized stay suggestions based on user search history.
- [ ] **Calendar Availability Picker**: Interactive date-range selection with conflict prevention.

---

## 🤝 Author & License

Developed with ❤️ by **[Anant Srivastava](https://github.com/BinaryBlaze16)**

- 💼 **LinkedIn**: [Anant Srivastava](https://www.linkedin.com/in/anant-srivastava-1b7465326/)
- 📧 **Email**: [binaryblaze16@gmail.com](mailto:binaryblaze16@gmail.com)
- 🐦 **X (Twitter)**: [@BinaryBlaze16](https://x.com/BinaryBlaze16)

Distributed under the **MIT License**. See `LICENSE` for more information.
