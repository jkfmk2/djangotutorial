# Project Context: Django Tutorial (Polls App)

## Overview
This is a standard Django tutorial project featuring a "Polls" application. It allows users to view questions and vote on choices. The project is containerized using Docker.

## Technology Stack
- **Framework:** Django 6.0.3
- **Language:** Python
- **Database:** SQLite (`db.sqlite3`)
- **Containerization:** Docker, Docker Compose
- **Timezone:** Asia/Taipei

## Key Components

### Applications
- **`mysite`**: The project configuration folder.
  - `settings.py`: Main settings (INSTALLED_APPS, DATABASES, etc.).
  - `urls.py`: Root URL routing.
- **`polls`**: The main application.
  - `models.py`: Defines `Question` and `Choice` models.
  - `views.py`: Contains `IndexView`, `DetailView`, `ResultsView` (generic views), and `vote` (function view).
  - `urls.py`: App-specific URL routing.
  - `admin.py`: Registers `Question` model for the admin interface.

### Infrastructure
- **`manage.py`**: Django's command-line utility for administrative tasks.
- **`requirements.txt`**: Python dependencies.
- **`docker-compose.yml`**: Defines the `web` service running the Django dev server on port 8000.
- **`Dockerfile`**: Builds the Python environment.

## Setup & Usage

### Running with Docker (Recommended)
```bash
docker-compose up --build
```
The application will be available at `http://localhost:8000`.

### Running Locally
1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
2. **Apply migrations:**
   ```bash
   python manage.py migrate
   ```
3. **Run the server:**
   ```bash
   python manage.py runserver
   ```

### Running Tests
To run the automated tests for the `polls` app:
```bash
python manage.py test polls
```

## Development Notes
- **Views:** The project uses Django's Generic Views (`ListView`, `DetailView`) for standard pages and a function-based view for the `vote` action.
- **F-Expressions:** The `vote` view uses `F('votes') + 1` to prevent race conditions during vote counting.
- **Templates:** Templates are located in `polls/templates/polls/`.
