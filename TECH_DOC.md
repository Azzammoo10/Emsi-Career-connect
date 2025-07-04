# 📘 Documentation Technique – EMSI Career Connect

---

## 🧩 Vue d’ensemble

**EMSI Career Connect** est une application web MERN (MongoDB, Express.js, React.js, Node.js) déployée sur Azure.  
Elle combine deux modules principaux :
- 🔗 **Réseau social** pour lauréats
- 💼 **Plateforme de recrutement** pour recruteurs et administrateurs

---

## 👥 Rôles et permissions

| Rôle         | Accès                                                  |
|--------------|---------------------------------------------------------|
| **Lauréat**  | Voir/postuler offres, modifier profil, messagerie      |
| **Recruteur**| Créer offres, gérer candidatures, consulter profils    |
| **Admin**    | Gérer utilisateurs, offres, candidatures, validation   |

---

## 🔒 Variables d’environnement (.env)

Voici les clés à inclure dans le fichier `.env` :

```env
# Serveur
PORT=

# Environnement (development ou production)
NODE_ENV=

# MongoDB
MONGO_URI=

# Authentification JWT
JWT_SECRET=

# Mailtrap (notifications email)
MAILTRAP_TOKEN=
EMAIL_FROM=
EMAIL_FROM_NAME=

# Cloudinary (uploads images/documents)
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=
CLOUDINARY_CLOUD_NAME=

# Frontend (URL client)
CLIENT_URL=

# Giphy API (chatbot emojis)
VITE_GIPHY_API_KEY=

# Azure Blob Storage
AZURE_STORAGE_CONNECTION_STRING=

# OpenRouter (chatbot IA)
OPENROUTER_API_KEY=
```

> 🔐 **Important** : Ne jamais versionner ce fichier dans Git (`.gitignore`). Utilisez des secrets pour GitHub Actions en production.

---

## 📡 Exemple de routes API

### 🔐 Authentification

| Méthode | Route               | Description                     |
|--------|---------------------|---------------------------------|
| POST   | `/api/v1/auth/login` | Connexion utilisateur           |
| POST   | `/api/v1/auth/signup`| Inscription (lauréat/recruteur)|
| GET    | `/api/v1/auth/me`    | Infos utilisateur connecté      |

---

### 💼 Offres d’emploi

| Méthode | Route                            | Rôle        |
|--------|----------------------------------|-------------|
| POST   | `/api/v1/offres/`                | Recruteur   |
| GET    | `/api/v1/offres/`                | Public      |
| GET    | `/api/v1/offres/:id`             | Public      |
| POST   | `/api/v1/offres/:id/postuler`    | Lauréat     |

---

### 👤 Utilisateurs

| Méthode | Route                    | Description                     |
|--------|--------------------------|---------------------------------|
| GET    | `/api/v1/users/:id`      | Voir profil                     |
| PATCH  | `/api/v1/users/:id`      | Modifier profil (lauréat)       |
| GET    | `/api/v1/users`          | Admin – liste utilisateurs      |

---

## 🧠 Architecture technique (résumé)

```bash
emsi-career-connect/
├── backend/
│   ├── controllers/
│   ├── routes/
│   ├── models/
│   ├── middleware/
│   └── utils/
├── frontend/
│   ├── pages/
│   ├── components/
│   └── hooks/
└── .env
```

---

## 📌 Sécurité

- JWT stocké dans cookies HttpOnly
- Vérification des rôles via middlewares Express
- Uploads sécurisés (Cloudinary, Azure Blob)
- Protection CORS et rate limiting

---

## 📬 Contact technique

> Pour toute question ou support technique, contactez :  
📧 [azzam.moo@gmail.com](mailto:azzam.moo@gmail.com)
    