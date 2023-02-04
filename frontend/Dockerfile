# Specify base image (node:alpine)
FROM node:alpine as builder

# Working directory in the container
WORKDIR '/app'

# Copy the package.json file to the container working directory and install npm
COPY package.json .
RUN npm install

# Copy the rest of the files into the working directory of the container
COPY . .

# Command to build a production version of the React Application
RUN npm run build

FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html