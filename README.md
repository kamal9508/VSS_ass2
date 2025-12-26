# VideoVault — Enterprise Video Management (Local Dev)

VideoVault is a local, full‑stack demo app for secure video upload, automated sensitivity analysis, and streaming with role-based access control. This repository contains both the Vite + React frontend and a Node/Express backend with an in-memory fallback store (useful when MongoDB is not available).

![VideoVault Sign In](M:\Pulsegen\review-retriever-main\public\Login.png)

## Highlights

- Upload videos (local disk during dev)
- Background processing (ffmpeg used for metadata extraction)
- Sensitivity analysis placeholder (flagging heuristic)
- Streaming endpoint with HTTP Range support
- JWT auth with roles: `viewer`, `editor`, `admin`
- In-memory fallback store so you can demo without MongoDB

## Repository layout

- `src/` — Frontend (Vite + React + TypeScript)
- `server/` — Backend (Express, Socket.io, ffmpeg worker, in-memory fallback)
- `assets/` — Images and example media used in README

## Quickstart (local development)

Prerequisites:

- Node.js 18+ and npm (or bun if you prefer)
- Optional: MongoDB (if you want persistence rather than in-memory fallback)

1) Install dependencies

```bash
# from repo root
npm install
cd server
npm install
cd ..
```

2) Start backend (defaults to port `4000`)

```bash
cd server
npm run dev
```

Backend notes:
- If `MONGODB_URI` is set and MongoDB is reachable, the server will use MongoDB.
- If not, an in-memory store is used for users and videos (non-persistent).

3) Start frontend (defaults to port `8080`)

```bash
# from repo root
npm run dev
```

Open http://localhost:8080 in your browser.

## Using the app (auth flow)

- On first use, click the `Sign Up` tab and create an account (email + password).
- After successful signup, you will be automatically logged in.
- If you try to `Sign In` with an email that is not registered, the app will return **Invalid credentials**.

Example test credentials (for quick dev/testing you can create these locally):

- Email: `kamaleshd5096@gmil.com`
- Password: `Kamal@1304`

If you prefer to register via API (debugging), use:

```bash
curl -X POST http://localhost:4000/auth/register \
  -H 'Content-Type: application/json' \
  -d '{"email":"you@example.com","password":"YourPassword123!"}'
```

Then login with:

```bash
curl -X POST http://localhost:4000/auth/login \
  -H 'Content-Type: application/json' \
  -d '{"email":"you@example.com","password":"YourPassword123!"}'
```

## Video upload and streaming

- Upload is implemented at `POST /api/videos/upload` (multipart form `file`).
- Streaming is available at `GET /api/videos/stream/:id` and supports `Range` headers for seeking.
- Processed video metadata and sensitivity flags are sent via Socket.io events.

## Environment variables

Create a `.env` file in `server/` to configure the backend as needed. Useful variables:

- `PORT` — backend port (default `4000`)
- `MONGODB_URI` — MongoDB connection string (optional)
- `JWT_SECRET` — secret used to sign JWT tokens (default in dev: `secret`)
- `UPLOAD_DIR` — path for uploaded files (default: `server/uploads`)

## Troubleshooting

- Invalid credentials on Sign In: make sure you registered first (Sign Up).
- If MongoDB connection fails, the server will log a connection error and fall back to in-memory storage — this is expected in a dev environment.
- If video upload fails, check `server/uploads/` exists and is writable.

## Next steps / Production

- Replace the local upload storage with S3 (or other cloud storage).
- Use MongoDB Atlas (or another managed DB) for persistence — set `MONGODB_URI`.
- Harden JWT secret and rotate tokens properly.
- Add automated sensitivity scanning (ML model) for production safety.

## Credits

This project was bootstrapped and extended for demonstration purposes.

---

If you'd like, I can also:

- Add the exact screenshot image you attached into `assets/` (please confirm you want that filename), or
- Replace the placeholder asset with your original screenshot file if you upload it to the repo root or provide the image file.
# Welcome to your Lovable project

## Project info

**URL**: https://lovable.dev/projects/REPLACE_WITH_PROJECT_ID

## How can I edit this code?

There are several ways of editing your application.

**Use Lovable**

Simply visit the [Lovable Project](https://lovable.dev/projects/REPLACE_WITH_PROJECT_ID) and start prompting.

Changes made via Lovable will be committed automatically to this repo.

**Use your preferred IDE**

If you want to work locally using your own IDE, you can clone this repo and push changes. Pushed changes will also be reflected in Lovable.

The only requirement is having Node.js & npm installed - [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating)

Follow these steps:

```sh
# Step 1: Clone the repository using the project's Git URL.
git clone <YOUR_GIT_URL>

# Step 2: Navigate to the project directory.
cd <YOUR_PROJECT_NAME>

# Step 3: Install the necessary dependencies.
npm i

# Step 4: Start the development server with auto-reloading and an instant preview.
npm run dev
```

**Edit a file directly in GitHub**

- Navigate to the desired file(s).
- Click the "Edit" button (pencil icon) at the top right of the file view.
- Make your changes and commit the changes.

**Use GitHub Codespaces**

- Navigate to the main page of your repository.
- Click on the "Code" button (green button) near the top right.
- Select the "Codespaces" tab.
- Click on "New codespace" to launch a new Codespace environment.
- Edit files directly within the Codespace and commit and push your changes once you're done.

## What technologies are used for this project?

This project is built with:

- Vite
- TypeScript
- React
- shadcn-ui
- Tailwind CSS

## How can I deploy this project?

Simply open [Lovable](https://lovable.dev/projects/REPLACE_WITH_PROJECT_ID) and click on Share -> Publish.

## Can I connect a custom domain to my Lovable project?

Yes, you can!

To connect a domain, navigate to Project > Settings > Domains and click Connect Domain.

Read more here: [Setting up a custom domain](https://docs.lovable.dev/features/custom-domain#custom-domain)
