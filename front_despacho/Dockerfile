# Etapa 1: Build (Construcción)
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Etapa 2: Producción (Servidor Web Nginx)
FROM nginx:alpine
# Copiamos los archivos estáticos de Vite al directorio de Nginx
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]