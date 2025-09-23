# Restaurant Guide App

A guide-like single-page application (SPA) introducing users to various restaurants. The app features a user-friendly frontend and a backend that interacts with the Google Places API, treating it as a structured database.


## User Flow

1. Open Web App
   - The user opens the web app in their browser.

2. Search for a Location/City/Area
   - The user enters a location, city, or area in the search bar.

3. View List of Restaurants
   - A list of restaurants in the specified location will appear on the page.

4. Click on a Restaurant Card
   - The user clicks on any restaurant card from the list to view more details.

5. Detailed Restaurant View
   - A new page opens, displaying detailed information about the selected restaurant.
     - The page includes the restaurant's name, description, contact details, and location.
     - The location is displayed on an interactive map.

## Features

### Frontend

- Single-page React app built with Next.js and TypeScript.
- Overview page showing a list of restaurants.
- Detailed restaurant page with additional information.
- Map integration showing restaurant locations.

### Backend

- Fastify server in Node.js with TypeScript.
- Routes for fetching all restaurants and fetching a specific restaurant.
- Integrates with Google Places API to provide restaurant data.
- Integrated with Google Geocoding API to get latitude and longitude of a place

### Additional Features

- Filters restaurants by criteria such as Rating, Open now, or Serves Beer.
- Containerized using Docker and orchestrated with Docker Compose.

## Tech Stack

- Frontend: Next.js, React, TypeScript
- Backend: Fastify, Node.js, TypeScript
- API: Google Places API
- Containerization: Docker, Docker Compose

## Getting Started

### Prerequisites

- Node.js 20+
- Docker Desktop and Docker Compose (if using containerization)
- Google Places API key

## With Docker

### Environment Variables

Create a `.env` file in your my-backend-app:

`PORT=3000`

`API_KEY=your_google_places_api_key`

Create a `.env` file for your infra folder:

`NEXT_PUBLIC_BACKEND_URL=http://backend:3000`

`API_KEY=your_google_places_api_key`

### Running

1. Build and start containers

```bash
  cd infra
  docker-compose up --build
```

2. Frontend: [http://localhost:3001](http://localhost:3001)
   Backend: [http://localhost:3000](http://localhost:3000)

## Without Docker (Local)

### Environment Variables

Create a `.env` file in your my-backend-app:

`PORT=3000`

`API_KEY=your_google_places_api_key`

Create a `.env` file for your my-frontend-app folder:

`NEXT_PUBLIC_BACKEND_URL= http://localhost:3000`

### Running Locally

1. Start the backend:

   ```bash
   cd my-backend-app
   npm install
   npx tsx src/index.ts
   ```

2. Start the frontend:

   ```bash
   cd my-frontend-app
   npm install
   npm run dev -- -p 3001
   ```

3. Open your browser at [http://localhost:3001](http://localhost:3001).

## Project Structure

```text
/project-root
├── my-frontend-app/              
├── my-backend-app/                
├── infra/                  # Infrastructure config (e.g. Docker)
│   └── docker-compose.yml   
└── README.md               # Project documentation

## API Endpoints

- `GET /restaurants` – Fetch all restaurants
- `GET /restaurants/:id` – Fetch a specific restaurant by ID
- `GET /health` – Health check endpoint

## Notes

- Ensure backend is running before accessing the frontend.
- Client-side code accesses the backend through `NEXT_PUBLIC_BACKEND_URL`.
- Backend must listen on `0.0.0.0` for container networking.
