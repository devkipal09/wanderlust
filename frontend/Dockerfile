# Use Node.js base image
FROM node:21 AS backend-builder

# Set working directory inside the container
WORKDIR /app

# Copy package.json and install dependencies
COPY . .
RUN npm install

#test
RUN npn run test


#state2
FROM node:21-slim

WORKDIR /app

# Copy the entire source code
COPY --from=backend-builder /app .

COPY .env.docker .env
# Expose the app port
EXPOSE 5000

# Command to run the app
CMD ["npm", "start"]
