# Restaurant Guide App

A guide-like single-page application (SPA) introducing users to various restaurants. The app features a user-friendly frontend and a backend that interacts with the Google Places API, treating it as a structured database.

## Features

### Frontend

- Single-page React app built with Next.js and TypeScript.
- Overview page showing a list of restaurants.
- Detailed restaurant cards with additional information.
- Optional map integration showing restaurant locations.

### Backend

- Fastify server in Node.js with TypeScript.
- Routes for fetching all restaurants and fetching a specific restaurant.
- Integrates with Google Places API to provide restaurant data.

### Optional / Additional Features

- Filters restaurants by criteria such as type, location, or date.
- Containerized using Docker and orchestrated with Docker Compose.

## Tech Stack

- Frontend: Next.js, React, TypeScript
- Backend: Fastify, Node.js, TypeScript
- API: Google Places API
- Containerization: Docker, Docker Compose

## Getting Started

### Prerequisites

- Node.js 18+
- Docker and Docker Compose (if using containerization)
- Google Places API key

### Environment Variables

Create a `.env` file for your backend:
PORT=3000
API_KEY=your_google_places_api_key

Create a `.env` file for your frontend:
NEXT_PUBLIC_BACKEND_URL=http://localhost:3000

### Running Locally (Without Docker)

1. Start the backend:
   cd backend
   npm install
   npx tsx src/index.ts

2. Start the frontend:
   cd frontend
   npm install
   npm run dev -- -p 3001

3. Open your browser at [http://localhost:3001](http://localhost:3001).

### Running with Docker

1. Build and start containers:
   docker-compose up --build
2. Frontend: [http://localhost:3001](http://localhost:3001)
   Backend: [http://localhost:3000](http://localhost:3000)

## Project Structure

/project-root
/frontend # Next.js React app
/backend # Fastify backend
/infra/docker-compose.yml
README.md

## API Endpoints

- `GET /restaurants` – Fetch all restaurants
- `GET /restaurants/:id` – Fetch a specific restaurant by ID
- `GET /health` – Health check endpoint

## Notes

- Ensure backend is running before accessing the frontend.
- Client-side code accesses the backend through `NEXT_PUBLIC_BACKEND_URL`.
- Backend must listen on `0.0.0.0` for container networking.
