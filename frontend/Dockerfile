# Stage 1: Build Stage
FROM node:14-alpine AS builder
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Runtime Stage
FROM node:14-alpine
WORKDIR /usr/src/app
COPY --from=builder /usr/src/app/build ./build
RUN npm install -g serve
EXPOSE 3000
CMD ["serve", "-s", "build", "-l", "3000"]

