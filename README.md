# VideoVault — Enterprise Video Management

VideoVault is a full-stack demo application for secure video upload, automated sensitivity analysis, and streaming with role-based access control. The platform allows authenticated users to upload videos, monitor real-time processing progress, detect whether a video is safe or flagged, stream videos efficiently, and manage access based on roles (`viewer`, `editor`, `admin`). Think of it as a mini YouTube + content moderation system for enterprises.

![Login Page](public/Login.png)

## Features

- **Video Upload:** Upload videos locally (development) or to a cloud storage for production.
- **Real-Time Processing:** Monitor live progress of video processing using Socket.io.
- **Sensitivity Analysis:** Automatically flag unsafe content using placeholder heuristic (can integrate ML models).
- **Streaming Service:** Efficient video playback with HTTP Range support for seeking.
- **Role-Based Access Control:** JWT authentication with roles `viewer`, `editor`, `admin`.
- **Multi-Tenant Architecture:** Users can only access their own content; data is securely isolated.
- **Responsive Frontend:** Built with React + Vite + Tailwind CSS for cross-platform compatibility.

## Repository Structure

VideoVault/
│
├── server/ # Backend (Express + Socket.io)
├── src/ # Frontend (React + Vite)
├── public/ # Static assets (Login.png)
├── .gitignore
├── README.md
└── package.json

shell
Copy code

## Quickstart (Local Development)

### Prerequisites

- Node.js 18+ and npm
- Optional: MongoDB (for persistent storage; otherwise in-memory fallback is used)

### Install Dependencies

```bash
# From repo root
npm install
cd server
npm install
cd ..
Start Backend (Port 4000 by default)
bash
Copy code
cd server
npm run dev
Start Frontend (Port 8080 by default)
bash
Copy code
npm run dev
Open http://localhost:8080 in your browser.

Using the App
Sign Up: Create an account with email and password.

Sign In: Login using your credentials.

Upload Video: Navigate to dashboard and upload videos.

Streaming: Click on a video to play; seeking is supported.

Role Management: Features are restricted based on your assigned role (viewer, editor, admin).

Example Test Credentials
Email: kamaleshd5096@gmil.com

Password: *******

Environment Variables
Create a .env file in server/:

ini
Copy code
PORT=4000
MONGODB_URI=<your_mongodb_connection_string>
JWT_SECRET=secret
UPLOAD_DIR=server/uploads
Next Steps / Production Enhancements
Replace local storage with AWS S3 or cloud storage.

Implement automated ML-based sensitivity scanning.

Harden JWT secrets and implement token rotation.

Use MongoDB Atlas or another managed DB for persistence.

Credits
This project was bootstrapped for demonstration purposes and extended to showcase a full-stack video management system with real-time processing.
