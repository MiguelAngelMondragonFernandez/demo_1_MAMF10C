# Fase uno: Construcción de los recursos/dependencias
FROM node:20 as build

WORKDIR /app

COPY package*.json ./


RUN npm install

COPY . .

RUN npm run build

# Fase dos: Para construir la imagen

FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]