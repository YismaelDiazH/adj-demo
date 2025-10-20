#Etapa 1
FROM node:20 as build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .
 #VIENEN DE DOCKERCOMPOSE
ARG API_HOST
ARG API_PORT
ARG API_BASE

ENV VITE_API_HOST=$API_HOST
ENV VITE_API_PORT=$API_PORT
ENV VITE_API_BASE=$API_BASE

RUN npm run build

#Etapa 2: imagen
FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

#un solo comando 
CMD ["nginx", "-g", "daemon off;"]