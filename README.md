# Microservices Containerization — Docker Compose

Containerization of four Node.js microservices from the [Microservices-Task](https://github.com/mohanDevOps-arch/Microservices-Task) repository, orchestrated with Docker Compose.

---

## Architecture

| Service         | Port | Endpoints                                      |
|-----------------|------|------------------------------------------------|
| user-service    | 3000 | `GET /health`, `GET /users`                    |
| product-service | 3001 | `GET /health`, `GET /products`                 |
| order-service   | 3002 | `GET /health`, `GET /orders`, `POST /orders`   |
| gateway-service | 3003 | `GET /api/users`, `GET /api/products`, `GET /api/orders` |

---

## Prerequisites

- Docker Desktop
- Git

---

## Project Structure
---

## Setup Instructions

```bash
# Clone the repo
git clone https://github.com/anjali2430-hub/Microservices-Task.git
cd Microservices-Task

# Build and start all services
docker compose up --build
```

---

## Testing Each Service

```bash
# User Service
curl http://localhost:3000/users

# Product Service
curl http://localhost:3001/products

# Order Service
curl http://localhost:3002/orders

# Create an order
curl -X POST http://localhost:3002/orders \
  -H "Content-Type: application/json" \
  -d '{"userId": 1, "productId": 2}'

# Gateway - routes to all services
curl http://localhost:3003/api/users
curl http://localhost:3003/api/products
curl http://localhost:3003/api/orders
```

---

## Troubleshooting

- **Port already in use:** `lsof -ti:3000 | xargs kill -9` then retry
- **Container exits:** Check logs with `docker compose logs user-service`
- **Services can't reach each other:** All containers must be on `microservices-network`
- **Stale cache:** Run `docker compose build --no-cache`

---

## Screenshots

### All 4 containers running in Docker Desktop
![Docker Desktop](screenshots/Screenshot%202026-09-20%20at%207.40.35%20PM.png)

### Services starting up in terminal
![Services Starting](screenshots/Screenshot%202026-09-20%20at%207.41.09%20PM.png)

### curl responses from all endpoints
![curl responses](screenshots/Screenshot%202026-09-20%20at%207.41.41%20PM.png)

### POST order and GET orders
![Order created](screenshots/Screenshot%202026-09-20%20at%207.42.09%20PM.png)

