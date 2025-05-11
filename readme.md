# ContactHub

ContactHub is a Django and HTMX based contact manager application with file upload support and a modern, interactive UI powered by [HTMX](https://htmx.org/), [Tailwind CSS](https://tailwindcss.com/), and [DaisyUI](https://daisyui.com/). It supports user authentication, searching, and document uploads for each contact.

## Features

- User authentication (custom user model)
- Add, search, and delete contacts
- Upload and download documents for each contact
- Responsive UI with Tailwind CSS and DaisyUI
- Interactive actions using HTMX (AJAX-like behavior)
- S3 storage support for uploaded files (via django-storages)
- Ready for deployment on [Render.com](https://render.com/)

## Project Structure

```
contacthub/
    settings.py
    urls.py
    wsgi.py
    asgi.py
contacts/
    models.py
    forms.py
    views.py
    urls.py
    admin.py
    templates/
    static/
    migrations/
manage.py
requirements.txt
build.sh
render.yaml
```

## Getting Started

### Prerequisites

- Python 3.10+
- [pip](https://pip.pypa.io/en/stable/)
- [PostgreSQL](https://www.postgresql.org/) (for production)
- [Node.js](https://nodejs.org/) (optional, for Tailwind development)

### Installation

1. **Clone the repository:**
    ```sh
    git clone <your-repo-url>
    cd htmx-contacthub
    ```

2. **Create a virtual environment and activate it:**
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. **Install dependencies:**
    ```sh
    pip install -r requirements.txt
    ```

4. **Set up environment variables:**

    Create a `.env` file or set these in your environment:
    - `SECRET_KEY` (Django secret key)
    - `DATABASE_URL` (PostgreSQL connection string, e.g. `postgres://USER:PASSWORD@HOST:PORT/DBNAME`)
    - For S3 storage:
        - `AWS_S3_ACCESS_KEY_ID`
        - `AWS_S3_SECRET_ACCESS_KEY`
        - `AWS_STORAGE_BUCKET_NAME`
        - `AWS_S3_REGION_NAME`

5. **Apply migrations:**
    ```sh
    python manage.py migrate
    ```

6. **Create a superuser:**
    ```sh
    python manage.py createsuperuser
    ```

7. **Collect static files:**
    ```sh
    python manage.py collectstatic
    ```

8. **Run the development server:**
    ```sh
    python manage.py runserver
    ```

## Usage

- Visit [http://localhost:8000/](http://localhost:8000/) in your browser.
- Log in with your superuser credentials.
- Add, search, and manage your contacts.

## Deployment

This project is ready for deployment on [Render.com](https://render.com/):

- The [`render.yaml`](render.yaml) file defines the database and web service.
- The [`build.sh`](build.sh) script handles dependency installation, static file collection, and migrations.
- The app uses Gunicorn with Uvicorn worker for ASGI support.

## Custom User Model

The app uses a custom user model ([`contacts.models.User`](contacts/models.py)). If you add new apps or migrations, ensure you reference the correct user model.

## File Uploads

Uploaded documents are stored in S3 (production) or locally (development, if S3 is not configured). Only files with extensions `pdf`, `doc`, `docx`, or `txt` are allowed.

## Running Tests

```sh
python manage.py test
```

## License

MIT License

---

**Made with Django, HTMX, Tailwind CSS, and DaisyUI.**