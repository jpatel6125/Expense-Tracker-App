FROM node:16 AS build

WORKDIR /app

COPY ./frontend/package.json ./frontend/package-lock.json ./

RUN npm install

COPY ./frontend/ ./

RUN npm run build

# Stage 2: Serve the React app with Nginx
FROM nginx:alpine

COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]