FROM node:18-alpine3.18 as builder

WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM node:18-alpine3.18

WORKDIR /app

RUN npm install --global http-server
COPY --from=builder /app/build /app/build
CMD ["npx", "-y", "http-server", "-p", "8000", "/app/build"]
