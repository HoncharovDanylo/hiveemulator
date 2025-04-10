FROM node:latest AS build
EXPOSE 80
ARG VITE_API_BASE_URL_ARG


ENV VITE_API_BASE_URL $VITE_API_BASE_URL_ARG


WORKDIR /usr/src/app
COPY package.json package-lock.json ./
RUN npm install
COPY . .
RUN npm run build

#STAGE 2
FROM nginx:latest
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /usr/src/app/dist /usr/share/nginx/html