# Postgres Multiple Databases

This Docker image extends the official Postgres image to allow creation of
multiple databases during container initialization. Excellent for development and testing environments.

## Features

- Based on the latest official Postgres image
- Allows creation of multiple databases on startup
- Easy to use with a simple environment variable

## Usage

To use this image, run a container with the `POSTGRES_MULTIPLE_DATABASES` environment variable set to a comma-separated list of database names you want to create.

Example:

```bash
docker run -d \
  --name my-postgres \
  -e POSTGRES_PASSWORD=mysecretpassword \
  -e POSTGRES_MULTIPLE_DATABASES=db1,db2,db3 \
  wladpaiva/postgres-multiple-databases:latest
```

or using docker-compose:

```yaml
version: "3.8"
services:
  postgres:
    image: wladpaiva/postgres-multiple-databases:latest
    restart: always
    environment:
      POSTGRES_MULTIPLE_DATABASES: db1,db2,db3
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
    ports:
      - "5432:5432"
    volumes:
      - ./postgres-data:/var/lib/postgresql/data
```

This will create a Postgres instance with three databases: db1, db2, and db3.

## Environment Variables

`POSTGRES_MULTIPLE_DATABASES`: A comma-separated list of databases to create
All environment variables from the official Postgres image are also supported

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
