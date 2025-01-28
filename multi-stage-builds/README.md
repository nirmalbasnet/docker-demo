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


# Distroless Images

**Distroless images** are a type of minimal Docker image that contains only the **application** and its **runtime dependencies**, but **no package manager**, **shell**, or any unnecessary system components.

The idea behind **distroless images** is to minimize the size of the Docker image and improve security by eliminating components that are not necessary for the application to run. This helps reduce the attack surface and ensures that only what is required to execute the application is included in the container.

### **Key Characteristics of Distroless Images:**

1. **Minimal Base**: Distroless images are built on very minimal, optimized base images, usually with just the necessary libraries to run your application.
2. **No Package Managers or Shells**: They do **not** contain tools like `apt`, `yum`, or `bash` which are typically present in a standard image.
3. **Smaller Size**: Due to the lack of unnecessary components, distroless images are often much smaller in size compared to regular base images.
4. **Improved Security**: By stripping out unnecessary software, distroless images reduce the potential attack surface, making it harder for attackers to exploit vulnerabilities.

### **Example: Build the Node.js application**

1. Start by building the Node.js application in a separate build stage (using a fuller base image like `node`).
2. In the second stage, use the distroless image to create the final production-ready container.
```
  # Build Stage
  FROM node:18 AS build
  WORKDIR /app
  COPY package*.json ./
  RUN npm install
  COPY . .
  RUN npm run build

  # Distroless Stage
  FROM gcr.io/distroless/nodejs:18 as production
  WORKDIR /app
  COPY --from=build /app /app

  CMD ["index.js"]
```
