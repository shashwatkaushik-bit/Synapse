# Contributing to Synapse

Thank you for your interest in contributing to Synapse. This project is currently a small full-stack application with a FastAPI backend and a React + Vite frontend, and contributions that improve reliability, usability, and repository analysis are welcome.

## Getting Started

You can run the project locally using either native Python/Node or Docker.

### Option 1: Local Setup (Python & Node)

#### Backend

```bash
cd backend
python -m venv .venv
source .venv/Scripts/activate  # Git Bash on Windows
pip install -r requirements.txt
uvicorn main:app --reload
```

If you use PowerShell on Windows, activate the environment with:

```powershell
.venv\Scripts\Activate.ps1
```

#### Frontend

```bash
cd synapse-frontend
npm install
npm run dev
```

### Option 2: Docker Setup

```bash
docker-compose up --build
```

This will start both the backend on `http://localhost:8000` and the frontend on `http://localhost:5173`.

## What to Contribute

Good contributions include:

- Fixes for bugs in the clone flow or UI.
- Improvements to repository parsing and metadata extraction.
- Better error handling and user feedback.
- Documentation updates.
- Tests for backend behavior or frontend interactions.

If you want to work on a larger change, open an issue first so the approach can be discussed before implementation.

## Development Guidelines

- Keep changes small and focused.
- Follow the existing Python and React style already used in the repository.
- Avoid introducing unnecessary dependencies.
- Update the README or other docs when behavior changes.
- Do not commit generated artifacts such as `cloned_repo` or build output.

## Suggested Workflow

1. Fork the repository and create a feature branch.
2. Make your changes in a focused commit set.
3. Verify the backend and frontend still run locally.
4. Open a pull request with a clear description of what changed and why.

## Pull Request Checklist

- The change solves a specific problem or adds a clearly described feature.
- The code is readable and consistent with the rest of the project.
- Any relevant documentation has been updated.
- You have tested the change locally, or explained why testing was not possible.

## Reporting Issues

When filing an issue, please include:

- A short summary of the problem.
- Steps to reproduce.
- Expected and actual behavior.
- Relevant screenshots, logs, or request/response examples when available.

## Code of Conduct

Please keep communication respectful and constructive. Be welcoming to new contributors and assume good intent during review discussions.
