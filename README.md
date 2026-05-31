# 📝 Todo Python Web App

A robust, modern Todo Web Application built with **FastAPI**, **SQLModel** (SQLAlchemy + Pydantic), and **Jinja2 Templates**. It includes user authentication, CRUD task management, deadline validations, and automatic email notifications for high-priority tasks.

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100%2B-009688.svg)](https://fastapi.tiangolo.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🚀 Features

- **User Authentication**: Secure signup, login, and logout capabilities with session cookies and hashed passwords (using `bcrypt` & `passlib`).
- **Task Management (CRUD)**: Create, toggle completion, and delete tasks dynamically.
- **Task Metadata**: Set deadlines and priority levels (`High`, `Medium`, `Low`).
- **Deadline Validation**: Built-in validation prevents setting task deadlines in the past.
- **Email Notifications**: Automatic background email alerts (via Gmail SMTP) sent to the user when a **High** priority task is created.
- **Database Agnostic**: Support for local SQLite development and PostgreSQL for production deployments (e.g., Render/Heroku).
- **Clean UI**: Responsive layouts powered by standard HTML/CSS templates.

---

## 📂 Project Structure

```text
├── app/
│   ├── __init__.py
│   ├── auth.py         # Password hashing & verification helper functions
│   ├── database.py     # SQLModel connection & database initialization
│   ├── main.py         # FastAPI application entrypoint, routes, and email backend
│   ├── models.py       # SQLModel database schemas (User, Task, Status, Priority)
│   └── templates/      # Jinja2 HTML templates
│       ├── auth/
│       │   ├── login.html
│       │   └── signup.html
│       ├── base.html
│       ├── email_template.html
│       └── index.html
├── .gitignore
├── .python-version
├── LICENSE             # MIT License file
├── README.md           # Documentation
└── requirements.txt    # Python package dependencies
```

---

## 🛠️ Installation & Setup

Follow these steps to run the application locally:

### 1. Clone the Repository
```bash
git clone https://github.com/Yoge-2004/todo-python-app.git
cd todo-python-app
```

### 2. Create a Virtual Environment
Create a virtual environment using `uv`:
```bash
# Create environment
uv venv
```

To activate the virtual environment:
```bash
# macOS/Linux
source .venv/bin/activate

# Windows Command Prompt
.venv\Scripts\activate

# Windows PowerShell
.venv\Scripts\Activate.ps1
```

### 3. Install Dependencies
Install the required packages using `uv pip`:
```bash
uv pip install -r requirements.txt
```

---

## ⚙️ Configuration & Environment Variables

The app auto-detects its environment and configurations. To enable optional features like email notifications or custom databases, set the following environment variables:

| Variable | Description | Default |
| :--- | :--- | :--- |
| `DATABASE_URL` | Database connection URL. Connects to PostgreSQL if specified. | `sqlite:///./tasks.db` |
| `MAIL_USERNAME` | SMTP sender email username (e.g. Gmail). | *None (Email disabled)* |
| `MAIL_PASSWORD` | SMTP password (use a secure App Password for Gmail). | *None (Email disabled)* |

> [!NOTE]
> When `DATABASE_URL` is omitted, the app automatically initializes a local SQLite file named `tasks.db` inside the project root on startup.

> [!IMPORTANT]
> To send high-priority emails successfully, you must use a Google App Password (not your primary password) if you use Gmail as the SMTP relay.

---

## 🏃 Running the Application

Start the local Uvicorn development server using `uv run`:
```bash
uv run uvicorn app.main:app --reload
```
Once started, open your browser and navigate to:
👉 **[http://127.0.0.1:8000](http://127.0.0.1:8000)**

---

## 🧪 Development & Code Quality

To format and lint code before submitting contributions, you can run formatting and linting utilities using `uv`:
```bash
# Install development tools
uv pip install black isort flake8

# Run formatting and linting
uv run black .
uv run isort .
uv run flake8 app/
```

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for the full text.
