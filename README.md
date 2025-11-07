# 🧩 Git Basics Demo

## 🎯 Objectif

Ce mini-projet montre les bases de l’utilisation de **Git** et **GitHub**, à travers un scénario simple :
- Initialiser un dépôt local.
- Ajouter, modifier et suivre un fichier texte.
- Créer et fusionner une branche.
- Pousser les changements sur GitHub.
- Cloner le dépôt pour vérifier la synchronisation.

L’objectif est purement pédagogique : démontrer la maîtrise du **workflow Git complet**.

---

## 🧠 Étapes du projet

### 1️⃣ Initialiser le dépôt
```bash
mkdir git_basics_demo
cd git_basics_demo
git init
```

🎬 *Commentaire vidéo :*  
> “On crée un nouveau dossier et on initialise un dépôt Git.  
> Git va désormais suivre tous les changements à l’intérieur.”

---

### 2️⃣ Créer un premier fichier
```bash
echo "Version 1 - Hello Git" > notes.txt
git add .
git commit -m "Initial commit: ajout de notes.txt"
```

🎬 *Commentaire vidéo :*  
> “On crée notre premier fichier `notes.txt`, on l’ajoute à Git avec `git add`,  
> puis on valide ce changement avec `git commit`.”

---

### 3️⃣ Modifier le fichier
```bash
echo "Version 2 - Ajout d'une nouvelle ligne" >> notes.txt
git add notes.txt
git commit -m "Ajout d'une ligne dans notes.txt"
```

🎬 *Commentaire vidéo :*  
> “Chaque modification est enregistrée dans un commit,  
> ce qui permet de revenir en arrière ou de suivre l’évolution du projet.”

---

### 4️⃣ Visualiser l’historique
```bash
git log --oneline --graph
```

🎬 *Commentaire vidéo :*  
> “Avec `git log`, on peut visualiser les commits précédents, leur ordre et leurs identifiants.”

---

### 5️⃣ Créer une branche de test
```bash
git checkout -b feature_demo
echo "Version 3 - Branche feature_demo" >> notes.txt
git commit -am "Modifications sur la branche feature_demo"
git checkout master
git merge feature_demo
```

🎬 *Commentaire vidéo :*  
> “On crée une branche pour tester des modifications sans toucher la version principale.  
> Une fois les tests terminés, on fusionne la branche dans `master`.”

---

### 6️⃣ Créer le dépôt GitHub et pousser le code

Sur GitHub :
- Crée un dépôt **vide** nommé `git_basics_demo`.
- Copie l’URL SSH (recommandé) de ton dépôt :  
  `git@github.com:Holyblitz/git_basics_demo.git`

Puis, dans le terminal :

```bash
git remote add origin git@github.com:Holyblitz/git_basics_demo.git
git push -u origin master
```

🎬 *Commentaire vidéo :*  
> “On connecte le dépôt local à GitHub et on pousse la branche principale `master` en ligne.”

---

### 7️⃣ Cloner pour vérifier
```bash
cd ..
git clone git@github.com:Holyblitz/git_basics_demo.git cloned_repo
cd cloned_repo
cat notes.txt
```

🎬 *Commentaire vidéo :*  
> “On simule un poste distant pour vérifier que tout a bien été synchronisé sur GitHub.”

---

## 🔐 Authentification GitHub : Token ou clé SSH

Depuis quelque temps, GitHub **n’accepte plus les mots de passe classiques** pour `git push` en HTTPS.  
Il faut utiliser soit :

- un **Personal Access Token (PAT)** avec HTTPS,  
- soit une **clé SSH**, comme dans cette démo.

### ✅ Option 1 — Token personnel (HTTPS)

1. Aller sur GitHub → **Settings → Developer settings → Personal access tokens**.  
2. Créer un nouveau token (classic) avec au minimum le scope **`repo`**.  
3. Quand Git demande un “password” lors d’un `git push` :
   - Username = ton pseudo GitHub (`Holyblitz`)
   - Password = le **token**, pas ton mot de passe de compte.
4. (Optionnel) Mémoriser les identifiants :
   ```bash
   git config --global credential.helper store
   ```

### 🟣 Option 2 — Clé SSH (utilisée dans ce projet)

1. Générer une clé SSH :
   ```bash
   ssh-keygen -t ed25519 -C "ton_email_github@example.com"
   ```
   (Appuyer sur Entrée pour accepter le chemin par défaut `~/.ssh/id_ed25519`.)

2. Ajouter la clé à l’agent SSH :
   ```bash
   eval "$(ssh-agent -s)"
   ssh-add ~/.ssh/id_ed25519
   ```

3. Copier la clé publique :
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```

4. Sur GitHub → **Settings → SSH and GPG keys → New SSH key** :
   - Coller la clé publique,
   - Enregistrer.

5. Configurer le remote en SSH :
   ```bash
   git remote set-url origin git@github.com:Holyblitz/git_basics_demo.git
   git push -u origin master
   ```

Après ça, plus besoin de mot de passe ni de token à chaque `push` : la clé SSH gère l’authentification.

---

## 📦 Structure finale
```text
git_basics_demo/
├── README.md
└── notes.txt
```

---

## 🎥 Conseils de tournage

🎬 **Scène 1 (Terminal)**  
- Fond sombre, zoom léger pour la lisibilité.  
- Commandes tapées calmement, avec voix off ou sous-titres.  

🌐 **Scène 2 (Navigateur)**  
- Création du dépôt GitHub.  
- Affichage du dépôt après le `push`.  

🎵 **Musique :**  
- Bande-son légère type “lofi / focus / dev”.  

---

## 🧾 Licence
Projet open-source — librement réutilisable à des fins pédagogiques.
