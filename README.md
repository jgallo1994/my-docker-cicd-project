# My Docker CI/CD Project

## Overview

This project demonstrates a Node.js application with Docker and CI/CD integration. It includes a simple Express server with TypeScript, Docker setup for containerization, and basic CI/CD configuration.

## Project Structure

- `src/`: Contains the source code of the application.
- `Dockerfile`: Defines the Docker image build process.
- `docker-compose.yml`: Defines the services and configurations for Docker Compose.
- `package.json`: Contains the project dependencies and scripts.
- `tsconfig.json`: TypeScript configuration file.
- `jest.config.js`: Jest configuration for testing.
- `.dockerignore`: Specifies files to ignore when building the Docker image.

## Docker Setup

### Build the Docker Image

To build the Docker image for the application, run:

```
docker compose build

```

### Start the Application

To start the application using Docker Compose, run:

```bash
docker compose up
```

This will build and start the application in a Docker container. The application will be accessible at `http://localhost:3000`.

### Verify the Application

Once the application is running, open a browser or use a tool like `curl` to verify that the application is working. You can access it at:

```bash
http://localhost:3000
```

You should see the response from your Express server.

## Testing

To run tests using Jest, ensure you have the necessary dependencies installed. Use the following command:

```bash
npm test
```

This command will execute the test suite defined in your project and display the results in the terminal.

## CI/CD Integration

### GitHub Actions

To set up CI/CD with GitHub Actions:

1. Create a `.github/workflows` directory in your project root.
2. Add a workflow file, e.g., `ci.yml`, to define your CI/CD pipeline.

**Example `ci.yml` file:**

```yaml
name: CI

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'

    - name: Install dependencies
      run: npm install

    - name: Build application
      run: npm run build

    - name: Run tests
      run: npm test

    - name: Build Docker image
      run: docker compose build

    - name: Push Docker image
      run: docker compose push

```

### GitHub Actions Workflow

This workflow will:

1. Checkout the code from the repository.
2. Set up Node.js.
3. Install project dependencies.
4. Build the application.
5. Run the tests.
6. Build and push the Docker image.

## Running Locally

If you want to run the application locally without Docker, follow these steps:

1. Install dependencies:

    ```
     npm install
    ```

2. Build the TypeScript code:

    ```bash
     npm run build
    ```

3. Start the application:

    ```bash
     npm start
    ```


The application will be accessible at `http://localhost:3000`.

---