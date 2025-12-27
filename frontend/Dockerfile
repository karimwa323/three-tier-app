# Frontend Dockerfile - React
# Build stage
FROM node:18-alpine as builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

# Production stage
FROM node:18-alpine

WORKDIR /app

RUN npm install -g serve

COPY --from=builder /app/build ./build
COPY --from=builder /app/package*.json ./

EXPOSE 3000

CMD ["serve", "-s", "build", "-l", "3000"]
