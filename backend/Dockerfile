# Stage 1: Build Stage
FROM node:14 AS build
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .

# Stage 2: Runtime Stage
FROM node:14-alpine
WORKDIR /usr/src/app
COPY --from=build /usr/src/app /usr/src/app
EXPOSE 3500
CMD ["node", "index.js"]

