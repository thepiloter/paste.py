# paste.py 🐍

paste.py is a modern pastebin service written in Python using FastAPI. It allows users to share code snippets and text files through a web interface or REST API, with support for syntax highlighting, file uploads, and expiration times.

## Prerequisites

- [Git](https://git-scm.com/downloads)
- [Docker Desktop](https://docs.docker.com/desktop/)

## Local Setup

### Step 1: Clone and Setup
Clone the repository and navigate to project directory:
```bash
git clone https://github.com/thepiloter/paste.py.git
cd paste.py
```

### Step 2: Configure Environment
Create environment file from example:
```bash
cp .env.example .env
```
*The .env.example file already contains working default values suitable for local development.*

### Step 3: Start Services
Run the application using Docker Compose:
```bash
docker-compose up -d
```
*The first startup may take a few minutes as it downloads images and sets up the database.*

### Step 4: Access Application
Open your browser and navigate to: http://localhost:8082

The application provides:
- **Web Interface**: http://localhost:8082/web (paste creation form)
- **API Documentation**: http://localhost:8082/docs (interactive API docs)

## Usage

### Web Interface
Navigate to http://localhost:8082/web to create and share pastes through the browser interface.

### API Usage
Use curl or any HTTP client to interact with the REST API:

```bash
# Create a paste
curl -X POST "http://localhost:8082/api/paste" \
     -H "Content-Type: application/json" \
     -d '{"content": "Hello World", "extension": "txt"}'

# Upload a file
curl -X POST -F "file=@example.txt" http://localhost:8082/file
```

### Management Commands
Run application commands using docker compose:

```bash
# Run database migrations
docker compose exec myapp pdm run migrate

# Run tests
docker compose exec myapp pdm run test
```

## Container Management

```bash
# Stop containers (data persists)
docker compose stop

# Start containers
docker compose start

# Stop and remove containers
docker compose down
```

## Development Setup (Without Docker)

If you prefer to run the application directly:

### Prerequisites
- Python 3.10+ (3.11.3 recommended)
- [PDM](https://pdm.fming.dev/latest/)

### Setup
```bash
git clone https://github.com/thepiloter/paste.py.git
cd paste.py
pdm install
pdm run start
```

The application will be available at http://localhost:8080

## Contributing

Please read the [Code of Conduct](CODE_OF_CONDUCT.md) and [Contributing Guidelines](CONTRIBUTING.md) before contributing.

## License

This project is licensed under the MIT License.
