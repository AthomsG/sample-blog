---
layout: post
title: "How to Set Up PostgreSQL with Docker"
date: 2023-07-10
categories: tutorials database docker
excerpt: "A step-by-step guide to setting up a PostgreSQL database using Docker for local development."
---

# Setting Up PostgreSQL with Docker

Docker makes it incredibly easy to run PostgreSQL without installing it directly on your system. This approach is perfect for development environments and ensures consistency across teams.

## Prerequisites

- [Docker](https://www.docker.com/get-started) installed on your system
- Basic knowledge of terminal/command line

## Step 1: Pull the PostgreSQL Image

First, let's pull the official PostgreSQL image from Docker Hub:

```bash
docker pull postgres:latest
```

## Step 2: Run PostgreSQL Container

Now, let's run a container using this image:

```bash
docker run --name my-postgres-db -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
```

This command:
- Names the container `my-postgres-db`
- Sets the PostgreSQL password to `mysecretpassword`
- Maps port 5432 from the container to port 5432 on your local machine
- Runs the container in detached mode (in the background)

## Step 3: Verify the Container is Running

Check that your container is running with:

```bash
docker ps
```

You should see your container in the list.

## Step 4: Connect to Your Database

You can connect to your PostgreSQL database using any PostgreSQL client with these credentials:

- Host: localhost
- Port: 5432
- Username: postgres (default)
- Password: mysecretpassword
- Database: postgres (default)

## Step 5: Create a Database and Tables

Let's connect to the PostgreSQL shell:

```bash
docker exec -it my-postgres-db psql -U postgres
```

Now you can create a database:

```sql
CREATE DATABASE myapp;
\c myapp
```

Create a table:

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

Insert some data:

```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john@example.com');
```

Exit the PostgreSQL shell:

```sql
\q
```

## Step 6: Persisting Your Data

To ensure your data persists even if the container is removed, you should use a volume:

```bash
docker run --name my-postgres-db -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -v postgres_data:/var/lib/postgresql/data -d postgres
```

This creates a Docker volume called `postgres_data` that will store your database files.

## Step 7: Common Management Commands

Stop the container:
```bash
docker stop my-postgres-db
```

Start it again:
```bash
docker start my-postgres-db
```

Remove the container (warning: this will delete the container but not the volume):
```bash
docker rm my-postgres-db
```

## Step 8: Using Docker Compose (Recommended)

For a more maintainable setup, create a `docker-compose.yml` file:

```yaml
version: '3'

services:
  db:
    image: postgres:latest
    container_name: my-postgres-db
    environment:
      POSTGRES_PASSWORD: mysecretpassword
      POSTGRES_USER: postgres
      POSTGRES_DB: myapp
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

Then run:

```bash
docker-compose up -d
```

This accomplishes the same as our previous commands but in a more organized way.

## Conclusion

You now have a PostgreSQL database running in Docker! This setup is perfect for development environments and can easily be shared with teammates or included in your project documentation for consistent development experiences.
