# School API VIII

By the end of this assignment you will have a fully serviceable CRUD API with user authentication capabilities that will allow School staff to easily manage students and scholastic equipment.

## School API Front End

In this assignment you will construct a Vite + React.js Front-End application that will communicate with the Django School API to generate a friendly user interface.

## Tasks

- Add the field `id` to your Student Django Serializer
- Create a HomePage.jsx that will give users a welcome message to your school portal
- Create a SubjectsPage.jsx that will give users all information matching the Django API response from `http://127.0.0.1:8000/api/v1/subjects/` with a link to each individual subject.
- Create an ASubjectPage.jsx that will give users all information matching the Django API response from `http://127.0.0.1:8000/api/v1/subjects/<str:subject>/`.
- Create a StudentsPage.jsx that will give users all information matching the Django API response from `http://127.0.0.1:8000/api/v1/students/` with a link to each individual student.
- Create an AStudentPage.jsx that will give users all information matching the Django API response from `http://127.0.0.1:8000/api/v1/students/<int:id>/`.
- Create and Connect a Browser Router to your React Application to render each page on their own route.
- Create and Connect a Navigation Bar to give users the ability to move between pages

## Tools and Dependencies to Consider

- Vite + React
  - axios
  - React Hooks
  - React Router DOM
  - Browser Router Hooks

- Django API
  - CORS
  
## Running with Docker Compose

This project runs as two containers, **Django** (`server/`) and **PostgreSQL** (`db/`), started together with Docker Compose. Run every command below from the root of this repository (where `docker-compose.yml` lives).

```bash
# build the images and start both containers in the background
docker compose up -d --build

# open a shell inside the Django container
docker compose exec backend bash
```

Django commands must run **inside** the `backend` container, because `settings.py` reaches the database through the host name `db`:

```bash
# DOCKER CONTAINER TERMINAL
python manage.py migrate
python manage.py test
```

The API is served at [http://localhost:8000](http://localhost:8000). Useful commands:

| Command | What it does |
| ------- | ------------ |
| `docker compose ps` | Lists the containers and their status |
| `docker compose logs -f backend` | Follows Django's output |
| `docker compose down` | Stops and removes the containers (the database volume is kept) |
| `docker compose down -v` | Same, but also **deletes** the database volume |

> Whenever you `pip install` a new package, run `pip freeze > requirements.txt` inside `server/` (with your virtual environment active) and then `docker compose up -d --build` so the image gets the new package.
