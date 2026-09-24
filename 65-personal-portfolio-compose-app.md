# 🚀 Personal Portfolio Compose

> A containerized personal portfolio built with Docker Compose, PHP, Apache, and PostgreSQL.

**Personal Portfolio Compose** is a simple containerized web application that combines PHP, Apache, and PostgreSQL into a single Docker Compose project.

The project was created as a practical lab to understand how multiple Docker services communicate, share configuration, and work together as one application.

---

## 📌 Project Overview

| Component | Technology |
|-----------|------------|
| 🐳 Containerization | Docker |
| ⚙️ Orchestration | Docker Compose |
| 🌐 Web Server | Apache |
| 🐘 Backend | PHP 8.2 |
| 🗄️ Database | PostgreSQL 15 |
| 🎨 Frontend | HTML & CSS |
| 🔗 Communication | Docker Network |
| 💾 Storage | Docker Volume |

---

## 🏗️ Architecture

The project contains two main services:

| Service | Purpose | Port |
|---------|---------|------|
| `portfolio-web` | Runs PHP + Apache | `8080:80` |
| `portfolio-db` | Runs PostgreSQL | `5432` internally |

The two containers communicate through the custom Docker network:

     portfolio-compose_portfolio-network   
   

PostgreSQL data is stored using the Docker volume:

    portfolio-compose_db-data

![alt text](<Screenshot From 2026-09-24 07-54-19.png>)
---

## 📁 Project Structure

    portfolio-compose/
    ├── .env
    ├── .env.example
    ├── .gitignore
    ├── Dockerfile
    ├── docker-compose.yml
    ├── README.md
    ├── db/
    │   └── init.sql
    └── src/
        └── index.php

---

## 🗄️ Database

The PostgreSQL database is automatically initialized using:

    db/init.sql

### Check the db folder if you want to check in database/init.sql

### Database Details

| Item | Value |
|------|-------|
| Database | `verventech` |
| User | `sumaid` |
| Main Table | `verventech` |
| Leaderboard View | `verventech_leaderboard` |

The database view provides:

- 🏆 Student ranking
- 📚 Completed labs
- 📋 Total labs
- ⏳ Remaining labs
- 💬 Student commentary


---

## 🔐 Environment Configuration

Database credentials are managed through environment variables instead of being hardcoded into PHP.

Example:

    POSTGRES_USER=sumaid
    POSTGRES_PASSWORD=change_me
    POSTGRES_DB=verventech

The `.env` file is excluded from Git using `.gitignore`

![alt text](<Screenshot From 2026-09-23 14-07-19.png>)


---

## ⚙️ How the Application Works

The application uses two connected Docker services:

    Docker Compose
          │
          ├── portfolio-web
          │       │
          │       └── PHP + Apache
          │
          └── portfolio-db
                  │
                  └── PostgreSQL
                          │
                          └── verventech database

PHP connects to PostgreSQL using environment variables supplied by Docker Compose.

The application then retrieves the required data from PostgreSQL and displays it through the web interface.

---

## ▶️ Running the Project

Move into the project directory:

    cd portfolio-compose

Start the application:

    docker compose up -d

![alt text](<Screenshot From 2026-09-23 11-24-29.png>)

Check the containers:

    docker compose ps

![alt text](<Screenshot From 2026-09-23 14-01-32.png>)

Open the portfolio:

    http://localhost:8080

---

## 🖥️ Portfolio Dashboard

The web interface provides a visual overview of the portfolio and database information.

It includes:

| Section | Information |
|---------|-------------|
| 👨‍🎓 Students | Total number of students |
| 📚 Completed Labs | Total completed labs |
| 📈 Overall Progress | Combined completion percentage |
| 🏆 Leaderboard | Student rankings |
| ⏳ Remaining Labs | Labs still to complete |
| 🗄️ Database Status | PostgreSQL connection status |

![alt text](<Screenshot From 2026-09-23 12-45-33.png>)

---

## 🛑 Stopping the Project

Stop the running containers:

    docker compose down

To stop the containers and remove the database volume:

    docker compose down -v

---

## 🔄 Rebuilding the Project

If the Dockerfile or application configuration changes:

    docker compose up -d --build

---

## 🔒 Security Notes

- `.env` is excluded from Git.
- Database credentials are provided through environment variables.
- PostgreSQL is not exposed directly to the host.
- PHP communicates with PostgreSQL through the Docker network.
- `.env.example` is provided as a safe configuration template.

---

## 🎯 What This Lab Demonstrates

This project brings several Docker concepts together in one practical application:

-  Docker containerization
-  Docker Compose
-  Container networking
-  PostgreSQL
-  Apache + PHP
-  Docker volumes
-  Environment variables
-  Database initialization
-  PostgreSQL views
-  Service dependencies
-  Container health checks

---