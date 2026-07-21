# Stage 1 - Install dependencies
FROM node:20-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

# Stage 2 - Production image
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci --omit=dev

COPY --from=builder /app .

EXPOSE 5000

CMD ["npm", "run", "start"]
