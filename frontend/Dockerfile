# Stage 1: Build and test
FROM node:21 AS backend-builder

# Set working directory inside the container
WORKDIR /app

# Copy all files and install dependencies
COPY . .
RUN npm install

# ✅ FIXED: Typo (was `npn run test`)
RUN npm run test

# Stage 2: Production image
FROM node:21-slim

# Set working directory
WORKDIR /app

# Copy files from builder stage
COPY --from=backend-builder /app .

# Use a separate env file for Docker if needed
COPY .env.docker .env

# Expose app port (change this if your app uses a different port)
EXPOSE 5000

# Start the app
CMD ["npm", "start"]
