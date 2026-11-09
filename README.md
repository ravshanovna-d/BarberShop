<div align="center">

# ✂️ BarberShop API

**Backend for a barbershop booking platform: user accounts, verification and JWT authentication.**

![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-REST%20Framework-092E20?logo=django&logoColor=white)
![JWT](https://img.shields.io/badge/Auth-JWT-000000?logo=jsonwebtokens&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-ready-2496ED?logo=docker&logoColor=white)
![License](https://img.shields.io/badge/License-GPL--3.0-blue)

</div>

---

## 📌 Overview

BarberShop API is a Django REST Framework backend. It provides the account system for a barbershop application: users sign up with an **email or a phone number**, confirm the account with a **one-time code**, finish their profile and log in with **JWT tokens**.

## ✨ Features

- 📝 **Sign-up by email or phone** (`+998XXXXXXXXX` format validation)
- 🔢 **4-digit verification codes**, with an option to request a new one
- 🔐 **JWT authentication**: login, token refresh, logout (blacklisting)
- 👤 **Profile management**: name, username, password and profile photo upload
- 🔁 **Password reset** and a password generator endpoint
- 👥 **Roles**: ordinary user, manager, admin
- 📧 **HTML email templates** for account activation (Gmail SMTP)
- 🛠 **Jazzmin admin panel**, import/export, standardized API errors
- 🐳 **Docker** and a **Makefile** for common commands

## 🧰 Tech Stack

| Layer | Tools |
|---|---|
| Framework | Django, Django REST Framework |
| Auth | `djangorestframework-simplejwt` |
| Admin | `django-jazzmin`, `django-import-export` |
| Server | Uvicorn (ASGI), Gunicorn (WSGI), WhiteNoise |
| Config | `python-decouple` (`.env`) |
| DevOps | Docker, docker-compose, Makefile |

## 🔌 API Endpoints

All routes are under `/{API_V1_URL}user/`, for example `/api/v1/user/`.

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `signup/` | Register with email or phone |
| `POST` | `verify/` | Confirm the verification code |
| `GET` | `new-verify/` | Request a new verification code |
| `PUT/PATCH` | `/` | Update profile information |
| `PUT` | `photo/` | Upload or change profile photo |
| `POST` | `login/` | Get access and refresh tokens |
| `POST` | `login/refresh/` | Refresh the access token |
| `POST` | `logout/` | Blacklist the refresh token |
| `POST` | `reset-password/` | Reset password |
| `GET` | `generate-password/` | Generate a strong password |

## 🚀 Getting Started

### 1. Clone and configure

```bash
git clone https://github.com/ravshanovna-d/BarberShop.git
cd BarberShop
cp .env.example .env   # then fill in your values
```

For email sending, use a Gmail **App Password** in `EMAIL_HOST_PASSWORD`. [How to generate one](https://youtu.be/lSURGX0JHbA).

### 2. Run locally

```bash
python -m venv env
source env/bin/activate        # Windows: env\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver 0.0.0.0:1024
```

Or with the Makefile: `make i && make mig && make run`.

### 3. Run with Docker

```bash
docker compose up --build
```

The API runs at **http://localhost:1024** and the admin panel at **/admin/**.

## 📁 Project Structure

```
BarberShop/
├── apps/v1/
│   ├── users/        # models, serializers, views, urls for auth & profile
│   └── shared/       # base model, permissions, pagination, responses
├── core/             # settings, urls, asgi/wsgi
├── templates/email/  # activation email template
├── config.py         # environment variables
├── Dockerfile
├── docker-compose.yml
└── Makefile
```

## 🗺 Roadmap

- [ ] Barbers, services and appointment booking
- [ ] AI hairstyle recommendation ([AI_Hairstyle_recommender](https://github.com/ravshanovna-d/AI_Hairstyle_recommender))
- [ ] PostgreSQL in production
- [ ] Swagger / OpenAPI docs

## 📄 License

Distributed under the **GNU GPL v3.0** license. See [LICENSE](LICENSE).
