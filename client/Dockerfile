# Étape 1 : utiliser Node LTS
FROM node:lts-alpine

# Créer le répertoire de travail
WORKDIR /app

# Copier les fichiers package.json et package-lock.json
COPY package*.json ./

# Fix NPM pour éviter erreur 500
RUN npm config set registry https://registry.npmmirror.com
RUN npm config set strict-ssl false

# Installer les dépendances
RUN npm install

# Copier le reste du code
COPY . .

# Construire l'application React
RUN npm run build

# Installer un serveur léger pour servir la build
RUN npm install -g serve

# Exposer le port 3000
EXPOSE 3000

# Lancer le serveur
CMD ["serve", "-s", "build", "-l", "3000"]
