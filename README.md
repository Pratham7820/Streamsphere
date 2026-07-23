# 🌀 StreamSphere

StreamSphere is a short-form video sharing platform built with Next.js. Users can register, log in, upload short (Reels/Shorts-style) videos, and browse a feed of uploaded content — with video hosting and transformations powered by ImageKit.

## ✨ Features

- **Authentication** — Email/password auth via NextAuth (credentials provider), with hashed passwords using bcrypt.
- **Video upload** — Client-side upload flow to ImageKit with progress tracking, then metadata saved to MongoDB.
- **Video feed** — Fetches and lists all uploaded videos, sorted by most recent.
- **Auto-generated thumbnails** — Thumbnail URLs derived automatically from the uploaded video.
- **Optimized playback** — Videos stored with configurable transformation (dimensions, quality) for portrait/short-form playback.
- **Modern UI** — Built with Tailwind CSS and shadcn/ui (Radix primitives), with light/dark theming via `next-themes`.

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Framework | [Next.js 15](https://nextjs.org/) (App Router, Turbopack) |
| Language | TypeScript |
| Styling | Tailwind CSS v4, shadcn/ui, Radix UI |
| Auth | NextAuth.js (Credentials provider, JWT sessions) |
| Database | MongoDB with Mongoose |
| Media hosting | ImageKit (`@imagekit/next`) |
| Notifications | react-hot-toast, sonner |
## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- A MongoDB database (local or [Atlas](https://www.mongodb.com/atlas))
- An [ImageKit](https://imagekit.io/) account for video/media storage

### 1. Clone the repository

```bash
git clone https://github.com/Pratham7820/Streamsphere.git
cd Streamsphere
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env.local` file in the project root:

```env
# MongoDB
MONGODB_URL = your_mongodb_connection_string

# NextAuth 
NEXTAUTH_SECRET = your_nextauth_secret

# ImageKit
NEXT_PUBLIC_PUBLIC_KEY = your_imagekit_public_key
NEXT_PUBLIC_URL_ENDPOINT = your_imagekit_url_endpoint
IMAGEKIT_PRIVATE_KEY = your_imagekit_private_key
```

### 4. Run the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the app.


## 🔌 API Overview

| Method | Route | Description |
|---|---|---|
| `POST` | `/api/auth/register` | Register a new user |
| `POST` | `/api/auth/[...nextauth]` | NextAuth sign-in/session handling |
| `GET` | `/api/auth/imagekit-auth` | Get signed auth params for direct-to-ImageKit uploads |
| `GET` | `/api/video` | List all videos (newest first) |
| `POST` | `/api/video` | Create a new video entry (requires authentication) |
