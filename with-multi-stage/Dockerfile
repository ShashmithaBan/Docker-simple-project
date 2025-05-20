# --- Stage 1: Build stage ---
FROM node:14-alpine AS build

WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .

# --- Stage 2: Production (distroless) stage ---
FROM gcr.io/distroless/nodejs:14

WORKDIR /app
COPY --from=build /app /app

ENV NAME=simple-project
EXPOSE 3000
CMD ["index.js"]