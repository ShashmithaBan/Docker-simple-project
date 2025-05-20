# Simple Dockerized Node.js Project

This is a minimal Node.js application that runs on port `3000` and demonstrates how to use Docker for containerization, including a multi-stage build for lean and secure production images.

---

## 🧩 Features

- Minimal `Node.js` server
- Runs inside a Docker container
- Uses **multi-stage Docker builds**
- Compatible with `distroless` or `alpine` base images
- Exposes port `3000`

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/ShashmithaBan/Docker-simple-project.git
cd Docker-simple-project
```
## 2. Build the Docker image
```
docker build -t simple-project .
```
## 3. Run the container
```
docker run -p 3000:3000 simple-project
```

Next at the port 3000 you will get the web-app

<img width="1680" alt="Screenshot 2025-05-20 at 17 22 31" src="https://github.com/user-attachments/assets/07be6ff3-7659-4f0a-8987-94f7eae8da58" />

---

## 🧱 Project Structure

```
.
├── Dockerfile
├── index.js
├── package.json
└── README.md
```
---
## 🐳 Dockerfile (Multi-stage)

```
# Build stage
FROM node:14-alpine AS build
WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .

# Final stage
FROM gcr.io/distroless/nodejs:14
WORKDIR /app
COPY --from=build /app /app
EXPOSE 3000
CMD ["index.js"]
```
