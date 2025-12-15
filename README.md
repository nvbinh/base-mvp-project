### Technology Stack and Features
  ## FastAPI for the Python backend API.
    - SQLModel for the Python SQL database interactions (ORM).
    - Pydantic, used by FastAPI, for the data validation and settings management.
    - PostgreSQL as the SQL database.
  ## Next.js for the frontend.
    - Using TypeScript, hooks, Vite, and other parts of a modern frontend stack.
    - Tailwind CSS and shadcn/ui for the frontend components.
    - Playwright for End-to-End testing.
  ## Docker Compose for development and production.
  ## Secure password hashing by default.
  ## JWT (JSON Web Token) authentication.
  ## Tests with Pytest.


  ## Start the local development
  `docker compose watch`
  
  1. Frontend, built with Docker, with routes handled based on the path: http://localhost:3000

  2. Backend, JSON based web API based on OpenAPI: http://localhost:8000

  3. Automatic interactive documentation with Swagger UI (from the OpenAPI backend): http://localhost:8000/docs

  4. Adminer, database web administration: http://localhost:8080
