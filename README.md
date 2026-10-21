# Distributed Lovable Clone — Frontend

A React-based frontend for an AI-powered application development platform inspired by Lovable. This project provides a web interface for interacting with application projects and their files through backend APIs.

## Overview

The frontend is built with React and TypeScript and uses Vite for development and production builds. It communicates with backend services through HTTP APIs.

The frontend and backend are deployed as separate Kubernetes Deployments within the same Google Kubernetes Engine (GKE) cluster.

## Tech Stack

- **React** — User interface
- **TypeScript** — Type-safe development
- **Vite** — Frontend tooling and build process
- **Tailwind CSS** — Styling
- **shadcn/ui** — UI components
- **Docker** — Containerization
- **Nginx** — Production web server
- **Google Kubernetes Engine (GKE)** — Container orchestration

## Architecture

```text
User / Browser
      |
      v
React + TypeScript Frontend
      |
      | HTTP API Requests
      v
Backend API
      |
      v
Backend Services
```

The frontend and backend run as separate Kubernetes Deployments in the same GKE cluster. The frontend communicates with the backend through its configured API endpoint.

## Deployment

The frontend is containerized using Docker and served through Nginx. It is deployed to GKE using Kubernetes manifests.

The frontend build uses the `VITE_API_URL` environment variable to configure the backend API endpoint.

Example:

```env
VITE_API_URL=http://api.vaibhavshahi.in
```

Configure the appropriate API URL before building the production image. If the frontend is served over HTTPS, the API must also support HTTPS to avoid browser mixed-content restrictions.

## Run Locally

### Prerequisites

- Node.js
- npm
- Access to the backend API

### Install dependencies

```bash
npm install
```

### Configure the API

Create a `.env` file in the project root:

```env
VITE_API_URL=http://api.vaibhavshahi.in
```

### Start the development server

```bash
npm run dev
```

Open the local URL displayed in the terminal, typically `http://localhost:5173`.

### Build for production

```bash
npm run build
```

## Run with Docker

Build the image:

```bash
docker build -t lovable-frontend .
```

Start the container:

```bash
docker run --rm -p 8080:80 lovable-frontend
```

Open `http://localhost:8080` in your browser.

## Project Structure

```text
src/
├── components/
│   └── ui/
├── hooks/
├── lib/
├── pages/
├── App.tsx
└── main.tsx

public/
Dockerfile
package.json
vite.config.ts
```

- `components/` — Application and reusable UI components
- `hooks/` — Custom React hooks
- `lib/` — Utilities and API integration
- `pages/` — Page-level components
- `App.tsx` — Root application component
- `main.tsx` — Application entry point

## Author

**Vaibhav Shahi**

[GitHub Profile](https://github.com/vaibhavshahi10)
