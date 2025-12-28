# --- Étape 1 : Construction (Build) ---
FROM node:18-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
# Crée le dossier "build" avec les fichiers statiques (HTML/CSS/JS)
RUN npm run build

# --- Étape 2 : Serveur Web (Nginx) ---
FROM nginx:alpine
# On copie le dossier build vers le dossier public de Nginx
COPY --from=build /app/build /usr/share/nginx/html
# Nginx écoute sur le port 80 par défaut (dans le conteneur)
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]