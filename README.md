# VisualDerm — AI Skin Lesion Classifier

## Overview

VisualDerm is a full-stack AI web application that classifies skin lesions from dermoscopy images into 7 categories using a MobileNetV2 model trained on the HAM10000 dataset. Built for educational and research purposes.

---

## Architecture

```
┌─────────────────────┐
│   Browser (React)   │
│   Vite + Tailwind   │
└────────┬────────────┘
         │ HTTP (port 5173)
         ▼
┌─────────────────────┐
│  Node.js Express    │
│  Auth + API Gateway │
│    (port 5000)      │
└────────┬────────────┘
         │ HTTP (port 8000)
         ▼
┌─────────────────────┐
│  Django REST API    │
│ AI Inference + DB   │
│    (port 8000)      │
└────────┬────────────┘
         │
         ▼
┌─────────────────────┐
│   ONNX Runtime      │
│ MobileNetV2 Model   │
└─────────────────────┘
```

---

## Tech Stack

| Layer      | Technology                        |
|------------|-----------------------------------|
| Frontend   | React + Vite + TailwindCSS        |
| Middleware  | Node.js + Express + JWT           |
| Backend    | Python + Django + DRF             |
| Database   | SQLite                            |
| AI Model   | MobileNetV2 + ONNX Runtime        |
| Dataset    | HAM10000                          |

---

## 7 Lesion Classes

| # | Class | Full Name | Risk Level |
|---|-------|-----------|------------|
| 1 | mel | Melanoma | High |
| 2 | nv | Melanocytic Nevi | Low |
| 3 | bcc | Basal Cell Carcinoma | High |
| 4 | akiec | Actinic Keratoses / Intraepithelial Carcinoma | Medium |
| 5 | bkl | Benign Keratosis-like Lesions | Low |
| 6 | df | Dermatofibroma | Low |
| 7 | vasc | Vascular Lesions | Low |

---

## Model Performance

- **Architecture:** MobileNetV2 fine-tuned on HAM10000
- **Validation Accuracy:** 78.4%
- **Training Strategy:** 2-phase transfer learning
  - Phase 1: Train classification head with frozen base
  - Phase 2: Unfreeze top layers for fine-tuning
- **Export Format:** ONNX for cross-platform inference

---

## Prerequisites

- Node.js 18+
- Python 3.10+
- Git

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yoursmaddyy/VisualDerm.git
cd VisualDerm
```

### 2. Django Backend (AI Inference + Database)

```bash
cd backend-django

# Create and activate virtual environment
python -m venv venv310
# Windows
venv310\Scripts\activate
# macOS/Linux
source venv310/bin/activate

pip install -r requirements.txt

python manage.py migrate
python manage.py runserver
```

> Runs on `http://localhost:8000`

### 3. Node.js Middleware (Auth + API Gateway)

```bash
cd backend-node
npm install
node server.js
```

> Runs on `http://localhost:5000`

### 4. React Frontend

```bash
cd frontend
npm install
npm run dev
```

> Runs on `http://localhost:5173`

---

## API Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| POST | `/api/auth/register` | None | Register a new user account |
| POST | `/api/auth/login` | None | Login and receive JWT token |
| POST | `/api/predict` | JWT | Upload dermoscopy image for classification |
| GET | `/api/history` | JWT | Retrieve prediction history for logged-in user |

---

## Project Structure

```
VisualDerm/
├── frontend/                  # React + Vite + TailwindCSS
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── main.jsx
│   ├── index.html
│   └── package.json
│
├── backend-node/              # Express API Gateway + Auth
│   ├── routes/
│   ├── middleware/
│   ├── server.js
│   └── package.json
│
├── backend-django/            # Django REST + AI Inference
│   ├── api/
│   │   ├── ai/
│   │   │   ├── inference.py
│   │   │   └── model.onnx
│   │   ├── models.py
│   │   ├── serializers.py
│   │   └── views.py
│   ├── manage.py
│   └── requirements.txt
│
├── .gitignore
└── README.md
```

---

## Disclaimer

> **This application is for educational purposes only and is not a substitute for professional medical advice, diagnosis, or treatment. Always consult a qualified dermatologist or healthcare provider for any skin-related concerns.**
