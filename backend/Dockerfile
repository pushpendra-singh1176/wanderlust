# ---------- Stage 1 : Build ----------
FROM node:18-alpine AS backend-builder

WORKDIR /app

# copy only package files first
COPY package*.json ./

RUN npm install

# copy source code
COPY . .

# optional: run tests
# RUN npm test


# ---------- Stage 2 : Runtime ----------
FROM node:18-alpine

WORKDIR /app

# copy only required files from builder
COPY --from=backend-builder /app .

# env file (optional)
COPY .env.docker .env

# backend port
EXPOSE 5000

# start backend
CMD ["npm", "start"]
