# go-mux-postgresql-docker

A simple CRUD (Create, Read, Update, Delete) API for managing users, built using **Go**, **PostgreSQL**, **Docker**, and a basic front-end in **HTML**. This application allows you to create, update, delete, and retrieve users through a REST API, with a simple web interface to interact with the API.

## Table of Contents

- [Project Description](#project-description)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Front-End](#front-end)
- [Dependencies](#dependencies)
- [Contributing](#contributing)


## Project Description

This project provides a simple **User Management system** where:

- Users can be added with their name and email.
- Users can be retrieved, updated, or deleted by ID.
- The project is containerized with Docker for easy deployment.
- A basic front-end HTML interface to interact with the API. 

## Installation

### Prerequisites

Make sure you have the following installed on your system:

- **Docker**: You can download and install Docker from [here](https://www.docker.com/get-started).
- **Docker Compose**: Install Docker Compose from [here](https://docs.docker.com/compose/install/).
- **Go**: To build and run the Go code, you need Go installed. Follow the installation guide [here](https://golang.org/doc/install).
- **PostgreSQL**: This is handled by Docker in the setup, so no installation is needed locally.

### Steps to Install

1. Clone the repository:

   ```bash
   git clone https://github.com/Fahad-I-Khan/go-mux-postgresql-docker.git
   cd go-mux-postgresql-docker
2. Start the PostgreSQL database container:

    ```bash
    docker compose up -d go_db
    ```
    This will start the PostgreSQL container in detached mode (-d).
3. Build the Go app container:

    ```bash
    docker compose build
    ```

4. Start the Go app container:

    ```bash
    docker-compose up go-app
    ```

5. **CORS Handling**: To handle CORS issues when accessing the API from the front-end, we will need to run a simple Python HTTP server. Open a new terminal and navigate to the folder containing the index.html file.

6. Start the Python HTTP server:

    ```bash
    python3 -m http.server 8001
    ```
7. Open your browser and navigate to `http://localhost:8001`. You should see the front-end HTML page for the User Management system.

## Usage
Once the app is running, you can use the following features:
- **Create User:** Enter a name and email, then click "Create User".
- **Get All Users:** Click "Get All Users" to retrieve a list of all users in the database.
- **Update User:** Provide a user ID, name, and email to update an existing user.
- **Delete User:** Enter a user ID to delete a user from the database.

The API is available at `http://localhost:8000/users`, and it supports the following HTTP methods:

- **GET:** Retrieve all users or a specific user by ID.
- **POST:** Create a new user.
- **PUT:** Update an existing user.
- **DELETE:** Delete a user by ID.

## API Endpoints
The following endpoints are available:

`GET /users`
- **Description:** Retrieve all users from the database.
- **Response:** An array of users in JSON format.

`GET /users/{id}`
- **Description:** Retrieve a single user by ID.
- **Response:** A user object in JSON format.

`POST /users`
- **Description:** Create a new user.
- **Body:** 

```json
{
  "name": "John Doe",
  "email": "johndoe@example.com"
}
```
- **Response:** The created user object in JSON format.

`PUT /users/{id}`
- **Description:** Update an existing user by ID.
- **Body:** 

```json
{
  "name": "John Updated",
  "email": "johnupdated@example.com"
}
```
- **Response:** The updated user object in JSON format.

`DELETE /users/{id}`
- **Description:** Delete a user by ID.
- **Response:** A message confirming the deletion, e.g., "User deleted".

## Front-End
The project includes a simple HTML page to interact with the API. The front-end is located in the `index.html` file and includes forms to create, update, and delete users, as well as a button to fetch all users.

## HTML Form Features:
- **Create User Form:** Allows you to create a new user by entering a name and email.
- **Update User Form:** Allows you to update a user's name and email by providing their user ID.
- **Delete User Form:** Allows you to delete a user by their user ID.
- **Get All Users:** Displays a list of all users.

To use the front-end, just open index.html in your browser.

## Dependencies
To build and run this project, the following dependencies are required:

- **Go:** The Go programming language (for the API).
- **PostgreSQL:** The database used to store user data.
- **Docker:** For containerizing the application.
- **Python 3:** For running the Python HTTP server to handle CORS.

## Go Dependencies:
In the go.mod file, the following Go packages are used:

- github.com/lib/pq: PostgreSQL driver for Go.
- github.com/gorilla/mux: Router for HTTP request handling.
- github.com/gorilla/handlers: For enabling CORS in the API.

To install these dependencies manually, run:

```bash
go mod tidy
```

## .dockerignore
The `.dockerignore` file tells Docker which files and directories to exclude when building an image, helping to reduce the image size and speed up the build process. It works similarly to a `.gitignore` file, preventing unnecessary files from being included in the container.

## Contributing
If you'd like to contribute to this project, follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
3. Make your changes.
4. Commit your changes and push them to your fork.
5. Open a pull request to the original repository.

## Project Structure
Here’s the structure of the project:
```bash
/go-mux-postgresql-docker
├── Dockerfile               # Dockerfile for building the Go API container
├── docker-compose.yml       # Docker Compose configuration file
├── .dockerignore            # Files to be ignored by Docker
├── main.go                  # Go source code for the API
├── go.mod                   # Go module dependencies
├── go.sum                   # Go module checksums
├── index.html               # Simple HTML frontend for user management
└── README.md                # Project documentation
```