 #!/bin/bash

echo "=== Création du projet React Sidrapicore ==="

npx create-react-app sidrapicore
cd sidrapicore

echo "=== Installation de i18n ==="
npm install i18next react-i18next i18next-browser-languagedetector

echo "=== Création des fichiers de traduction ==="
mkdir -p src/i18n

cat > src/i18n/fr.json <<EOL
{
  "welcome": "Bienvenue sur Sidrapicore",
  "login": "Se connecter",
  "logout": "Se déconnecter",
  "feed": "Fil d’actualité",
  "sendMessage": "Envoyer un message",
  "online": "En ligne",
  "wallet": "Portefeuille",
  "language": "Langue",
  "notifications": "Notifications"
}
EOL

cat > src/i18n/en.json <<EOL
{
  "welcome": "Welcome to Sidrapicore",
  "login": "Login",
  "logout": "Logout",
  "feed": "News Feed",
  "sendMessage": "Send Message",
  "online": "Online",
  "wallet": "Wallet",
  "language": "Language",
  "notifications": "Notifications"
}
EOL

cat > src/i18n/index.js <<EOL
import i18n from 'i18next';
import { initReactI18next } from 'react-i18next';
import LanguageDetector from 'i18next-browser-languagedetector';

import fr from './fr.json';
import en from './en.json';

i18n
  .use(LanguageDetector)
  .use(initReactI18next)
  .init({
    resources: {
      fr: { translation: fr },
      en: { translation: en }
    },
    fallbackLng: 'fr',
    interpolation: {
      escapeValue: false
    }
  });

export default i18n;
EOL

echo "=== Modification de src/index.js ==="
sed -i "1i import './i18n';" src/index.js

echo "=== Ajout d’un composant multilingue ==="
cat > src/App.js <<EOL
import React from 'react';
import { useTranslation } from 'react-i18next';
import './i18n';

function App() {
  const { t, i18n } = useTranslation();

  return (
    <div className="App">
      <h1>{t('welcome')}</h1>
      <button onClick={() => i18n.changeLanguage('fr')}>FR</button>
      <button onClick={() => i18n.changeLanguage('en')}>EN</button>
    </div>
  );
}

export default App;
EOL

echo "=== Initialisation Git + Push sur GitHub ==="
git init
git add .
git commit -m "Initial Sidrapicore app"
gh repo create sidrapicore --public --source=. --push

echo "=== Tout est prêt ! Va sur Vercel pour connecter ton projet GitHub ==="