 
#!/bin/bash

echo "=== Déploiement automatique de Sidrapicore ==="

# Étape 1 : Crée les fichiers nécessaires
echo "Création de package.json..."
cat > package.json <<EOL
{
  "name": "sidrapicore",
  "version": "1.0.0",
  "private": true,
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  }
}
EOL

echo "Création de vercel.json..."
cat > vercel.json <<EOL
{
  "version": 2,
  "builds": [
    { "src": "package.json", "use": "@vercel/static-build", "config": { "distDir": "build" } }
  ],
  "routes": [
    { "src": "/(.*)", "dest": "/" }
  ]
}
EOL

echo "Création de .env..."
cat > .env <<EOL
REACT_APP_API_URL=https://api.sidrapicore.com
REACT_APP_WALLET_PUBLIC_KEY=ton_wallet_public_key_ici
REACT_APP_SECRET_KEY=ta_clé_secrète_ultra_sécurisée
REACT_APP_DEFAULT_LANG=fr
REACT_APP_ENV=development
EOL

echo ".env" >> .gitignore

# Étape 2 : Ajout Git
git add package.json vercel.json .env .gitignore
git commit -m "Setup complet du projet Sidrapicore"
git push

echo "=== Terminé ! Les fichiers sont prêts et le dépôt est à jour ==="