# What is multi stage builds?

**Multi stage docker buids** are an advanced technique in Docker that allows us to create smaller, more efficient, and production-ready container images. By using multiple stages in a single Dockerfile, we can separate the build environment from the runtime environment, significantly reducing the size of the final image. The build stage is not the part of the final Docker image which helps in reducing the image size drastically. Only the final runtime stage is the part of the final Docker image.

Example:
```
  # Stage 1: Build Stage
  FROM ubuntu:latest as build
  WORKDIR /app

  RUN apt-get update && apt-get install -y nodejs npm

  COPY package*.json ./
  RUN npm install --frozen-lock --production
  COPY . .
  RUN npm run build

  # Stage 2: Runtime Stage
  FROM node:18-slim
  WORKDIR /app

  # Only copy the necessary files from the build stage
  COPY --from=build /app/dist /app/dist

  CMD ["node", "dist/index.js"]
```


