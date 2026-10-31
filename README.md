
# Appointment Booking & Scheduling API

API REST de gestion des rendez-vous développée avec Python, FastAPI et SQLite.

Ce projet permet de gérer les créneaux disponibles, les réservations, les annulations et les statuts des rendez-vous.

## 1. Technologies utilisées

- Python
- FastAPI
- SQLAlchemy
- SQLite
- Pydantic
- Uvicorn

## 2. Fonctionnalités

- Création des créneaux de disponibilité.
- Affichage de tous les créneaux.
- Consultation des créneaux disponibles.
- Réservation d'un rendez-vous.
- Vérification de la disponibilité avant réservation.
- Gestion des rendez-vous.
- Consultation d'un rendez-vous par son ID.
- Annulation d'un rendez-vous.
- Modification du statut d'un rendez-vous.
- Validation des données.
- Gestion des erreurs HTTP.

## 3. Structure du projet

```text
appointment_api/
│
├── main.py
├── database.py
├── models.py
├── schemas.py
├── requirements.txt
├── appointments.db
└── README.md
```

### Description des fichiers

| Fichier | Description |
|---|---|
| main.py | Routes et logique de l'API |
| database.py | Connexion à la base de données |
| models.py | Modèles et tables SQL |
| schemas.py | Validation des données |
| requirements.txt | Dépendances du projet |
| appointments.db | Base de données SQLite |

## 4. Installation

### Prérequis

- Python 3.10 ou supérieur
- pip
- Git (facultatif)

### Étape 1 : Cloner le projet

```bash
git clone https://github.com/VOTRE-USERNAME/appointment_api.git
```

Entrer dans le dossier :

```bash
cd appointment_api
```

### Étape 2 : Créer un environnement virtuel

```bash
python -m venv venv
```

### Étape 3 : Activer l'environnement virtuel

Sous Windows :

```bash
venv\Scripts\activate
```

Sous Linux / macOS :

```bash
source venv/bin/activate
```

### Étape 4 : Installer les dépendances

```bash
pip install -r requirements.txt
```

## 5. Lancer le serveur

Exécuter la commande suivante :

```bash
uvicorn main:app --reload
```

L'API sera accessible à l'adresse :

http://127.0.0.1:8000

## 6. Documentation de l'API

FastAPI génère automatiquement une documentation interactive.

Swagger UI :

http://127.0.0.1:8000/docs

ReDoc :

http://127.0.0.1:8000/redoc

Ces interfaces permettent de consulter et tester les endpoints.

## 7. Endpoints disponibles

### Gestion des créneaux

| Méthode | Endpoint | Description |
|---|---|---|
| POST | /slots | Créer un créneau |
| GET | /slots | Afficher tous les créneaux |
| GET | /slots/available | Afficher les créneaux disponibles |

### Gestion des rendez-vous

| Méthode | Endpoint | Description |
|---|---|---|
| POST | /appointments | Réserver un rendez-vous |
| GET | /appointments | Afficher tous les rendez-vous |
| GET | /appointments/{id} | Consulter un rendez-vous |
| PATCH | /appointments/{id}/cancel | Annuler un rendez-vous |
| PATCH | /appointments/{id}/status | Modifier le statut |

## 8. Exemples de requêtes

### Créer un créneau

POST /slots

```json
{
  "start_time": "2026-11-02T09:00:00",
  "end_time": "2026-11-02T10:00:00"
}
```

### Réserver un rendez-vous

POST /appointments

```json
{
  "customer_name": "Jean",
  "customer_email": "jean@gmail.com",
  "slot_id": 1
}
```

### Annuler un rendez-vous

PATCH /appointments/1/cancel

### Terminer un rendez-vous

PATCH /appointments/1/status

```json
{
  "status": "completed"
}
```

## 9. Gestion des statuts

Un rendez-vous possède deux statuts principaux :

| Statut | Description |
|---|---|
| confirmed | Rendez-vous confirmé |
| cancelled | Rendez-vous annulé |
| completed | Rendez-vous terminé |

## 10. Règles de gestion

L'API applique plusieurs règles :

- La date de début doit être antérieure à la date de fin.
- Un créneau ne peut pas être créé dans le passé.
- Deux créneaux ne peuvent pas se chevaucher.
- Un rendez-vous ne peut être réservé que sur un créneau disponible.
- Un créneau réservé devient automatiquement indisponible.
- Lorsqu'un rendez-vous est annulé, son créneau redevient disponible.
- Un rendez-vous terminé ne peut plus être annulé.

## 11. Base de données

Le projet utilise SQLite pour stocker les informations.

Deux tables principales sont utilisées :

**Table slots**
- id
- start_time
- end_time
- is_available

**Table appointments**
- id
- customer_name
- customer_email
- status
- slot_id

La relation entre les deux tables utilise une clé étrangère (`ForeignKey`).

## 12. Tests

Les endpoints peuvent être testés directement depuis Swagger UI :

http://127.0.0.1:8000/docs

Les principaux scénarios à tester :

- Création d'un créneau.
- Réservation d'un créneau disponible.
- Tentative de réservation d'un créneau déjà réservé.
- Annulation d'un rendez-vous.
- Réservation après annulation.
- Consultation d'un rendez-vous inexistant.
- Modification du statut d'un rendez-vous.

## 13. Objectif pédagogique

Ce projet a été réalisé dans le but de pratiquer :

- Le développement d'API REST avec FastAPI.
- La manipulation d'une base de données SQL.
- L'utilisation de SQLAlchemy.
- La validation des données avec Pydantic.
- La gestion des erreurs HTTP.
- L'implémentation de règles métier.
- Les opérations CRUD.

## 14. Auteur

**Tsiry**

Junior Backend Developer

Technologies : Python | FastAPI | SQL | SQLite

---

**Projet 4 — Appointment Booking & Scheduling API**
