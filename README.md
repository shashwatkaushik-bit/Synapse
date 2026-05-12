# Synapse

Synapse is a small full-stack app for cloning a GitHub repository from a URL. It uses a FastAPI backend for the clone request and a React + Vite frontend for the UI.

## What it does

- Accepts a repository URL in the frontend.
- Sends the URL to the backend at `http://127.0.0.1:8000/clone`.
- Clones the repository into `backend/cloned_repo` on the backend machine.
- Returns a success or failure message to the UI.

## Project Structure

- `backend/` - FastAPI service and repository cloning logic.
- `backend/main.py` - API entry point with the `/clone` route.
- `backend/app/cloner.py` - Git clone implementation.
- `backend/app/parser.py` - Placeholder for parsing logic.
- `backend/app/metadata.py` - Placeholder for metadata extraction.
- `synapse-frontend/` - React UI built with Vite.

## Tech Stack

- Backend: FastAPI, Pydantic, GitPython, Uvicorn
- Frontend: React 19, Vite

## Prerequisites

- Python 3.10+ recommended
- Node.js 18+ recommended
- Git installed and available on your system PATH

## Setup

### Option 1: Native Setup (Python & Node)

#### 1. Start the backend

```bash
cd backend
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

If you are using PowerShell on Windows, activate the virtual environment with:

```powershell
.venv\Scripts\Activate.ps1
```

The backend will run on `http://127.0.0.1:8000`.

#### 2. Start the frontend

```bash
cd synapse-frontend
npm install
npm run dev
```

The frontend will run on Vite's default development server, usually `http://127.0.0.1:5173`.

### Option 2: Docker Setup

Alternatively, run both services with Docker Compose:

```bash
docker-compose up --build
```

The backend will be available at `http://localhost:8000` and the frontend at `http://localhost:5173`.

## Usage

1. Open the frontend in your browser.
2. Paste a GitHub repository URL.
3. Click **Clone Repository**.
4. The app will call the backend and clone the repository into `backend/cloned_repo`.

## API

### `POST /clone`

Request body:

```json
{
  "url": "https://github.com/user/repository.git"
}
```

Success response:

```json
{
  "message": "Successfully cloned the repository."
}
```

Failure response:

```json
{
  "detail": "Cloning failed. Please check the URL."
}
```

## Notes

- The frontend currently shows clone progress and success/error state only.
- CORS is configured for the local Vite development origins used by the frontend.
- The clone target directory is removed and recreated on each request if it already exists.
- `parser.py` and `metadata.py` are present for future analysis features, but they are not wired into the current flow.

## Future Work

- Add repository parsing and metadata extraction.
- Persist cloned repository details and analysis results.
- Expand the UI beyond the current clone form and status display.
