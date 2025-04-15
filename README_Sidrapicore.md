# Sidrapicore

Application sociale React où les utilisateurs gagnent des Sidrapicores en partageant du contenu.

---

## 🚀 Déploiement sur Vercel

### 1. Préparer le projet

Assurez-vous que le projet fonctionne localement :

```bash
npm install
npm start
```

### 2. Créer un compte sur Vercel

- Allez sur [https://vercel.com](https://vercel.com)
- Connectez-vous avec GitHub (recommandé)

### 3. Pousser le projet sur GitHub

Si votre projet n’est pas encore sur GitHub :

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/votre-utilisateur/nom-du-repo.git
git push -u origin main
```

### 4. Déployer sur Vercel

1. Cliquez sur **"Add New Project"**
2. Sélectionnez le repo contenant Sidrapicore
3. Vercel détecte automatiquement que c’est une app React
4. Laissez les options par défaut :
   - **Framework preset** : React
   - **Build command** : `npm run build`
   - **Output directory** : `build`

### 5. Finaliser

- Cliquez sur **"Deploy"**
- Votre app est disponible sur : `https://nom-projet.vercel.app`

### 6. Mise à jour automatique

À chaque `git push`, Vercel redéploie automatiquement la dernière version.

---

## ✅ Astuce bonus

Vous pouvez connecter un nom de domaine personnalisé dans les paramètres du projet sur Vercel.

---

Fait avec amour pour la communauté Sidrapicore.
