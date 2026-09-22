# 🐳 Getting Started with Docker Compose

## What are we doing here?

In this lab, we will get a basic introduction to Docker Compose.

We will create a `compose.yaml` file, run an Apache container, access it through the browser, check the container, and then stop it.

---

## A quick idea about Docker Compose

Docker Compose lets us define and run Docker containers using a YAML file.

The configuration is written in:

`compose.yaml`

Instead of running a container manually with `docker run`, we can define the configuration once and use:

`docker compose up`

---

## 1. Create the project

Run:

`mkdir docker-compose-intro`

Then:

`cd docker-compose-intro`

Create the Compose file:

`nano compose.yaml`

Add:

`services:`

`  web:`

`    image: httpd`

`    ports:`

`      - "8090:80"`

Save the file.

---

## 2. Run the application

Check the Compose configuration:

`docker compose config`

Start the Apache container:

`docker compose up -d`

Check the running container:

`docker compose ps`

You should see:

`0.0.0.0:8090->80/tcp`

Now open the browser and visit:

`http://localhost:8090`

You should see the default Apache page.

---

## 3. Clean up

When finished, run:

`docker compose down`

---

## Things to remember

- `compose.yaml` contains the Docker Compose configuration.
- `services` defines the containers.
- `image: httpd` uses the Apache HTTP Server image.
- `8090:80` maps host port `8090` to Apache's container port `80`.
- `docker compose up -d` starts the service in the background.
- `docker compose ps` shows the running service.
- `docker compose down` stops and removes the container.

---

![alt text](<Screenshot From 2026-09-22 16-41-57.png>)

![alt text](<Screenshot From 2026-09-22 16-44-48.png>)
---

## Final Note

The basic Docker Compose workflow is:

`compose.yaml`

↓

`docker compose up -d`

↓

`Apache container`

↓

`localhost:8090`

Docker Compose becomes more useful when we have multiple containers that need to work together.