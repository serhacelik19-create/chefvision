# ChefVision AI

> **Status: Active Development** — Features are continuously being updated and improved.

A mobile-first recipe advisor that uses AI and computer vision to recognize kitchen ingredients from camera photos, generate personalized recipes, and guide users through cooking with a voice assistant. Users can manage their pantry, scan grocery receipts, track ingredient stock, and get hands-free cooking instructions.

Built with **Flutter** (mobile) and **FastAPI + PostgreSQL + Redis** (backend), powered by **Google Gemini Vision** for ingredient recognition.

This repository is a sanitized public version — all API keys, database credentials, and Firebase configurations have been removed.

---

## Features

### 🍳 Core Experience
- **Ingredient Scanner:** Camera-based workflow that captures photos of kitchen ingredients and uses Gemini Vision to identify them.
- **Recipe Engine:** AI-generated personalized recipes based on available ingredients, dietary preferences, and cooking skill level.
- **Cooking Mode:** Step-by-step cooking instructions with a built-in timer and completion tracking.
- **Voice Assistant:** Hands-free cooking guidance with speech-to-text commands and text-to-speech instruction reading.

### 🛒 Pantry & Shopping
- **Pantry Manager:** Track ingredient inventory with quantities, expiry awareness, and stock levels.
- **Receipt Scanner:** Photograph grocery receipts to automatically extract and add purchased items to the pantry.
- **Stock Analysis:** Visual dashboard of pantry contents, usage patterns, and low-stock alerts.
- **Shopping List:** Maintain and manage a shopping list synced with pantry needs.

### 👤 User Management
- **Auth System:** Registration, login, email verification, and profile editing.
- **Subscription Tiers:** Premium features gated behind subscription management (iyzico payment integration).
- **Guest Mode:** Limited access for users who want to explore before creating an account.
- **Notifications:** Push notifications via Firebase for recipe suggestions, stock reminders, and updates.

### 🌍 Localization
- Multi-language support: Turkish, English, German, French, Spanish, Italian — with full ARB-based localization infrastructure.

---

## Architecture

### Mobile App (Flutter)
```
lib/
├── screens/          # 16 screens (camera, cooking mode, pantry, recipes, auth, subscriptions...)
├── providers/        # State management (auth, recipe, timer, notification, guest, app)
├── models/           # Data models (recipe, ingredient, pantry, shopping, user, voice commands)
├── services/         # API clients, voice assistant, payment
├── config/           # API endpoints, theme
├── l10n/             # Localization files (6 languages)
└── utils/            # Error translation & localization
```

### Backend (FastAPI + Python)
```
backend/app/
├── routers/          # auth, recipes, ingredients, pantry, voice, subscription, admin, honeypot
├── services/         # gemini_vision, recipe_engine, voice_assistant, payment (iyzico), firebase, redis
├── core/             # encryption, rate_limiter, cache, logger, settings_store
├── models/           # SQLAlchemy ORM models
├── schemas/          # Pydantic validation schemas
└── tests/            # Router integration tests
```

---

## Tech Stack

| Component | Technologies |
|-----------|-------------|
| Mobile | Flutter, Dart, Camera API, Speech-to-Text, Text-to-Speech, Firebase |
| Backend | Python, FastAPI, SQLAlchemy, PostgreSQL, Redis |
| AI | Google Gemini Vision API |
| Payments | iyzico payment gateway |
| Auth | JWT + Firebase Admin SDK |

---

## Setup

### Backend
```bash
cd backend
docker-compose up -d              # Start PostgreSQL + Redis
python3.11 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env              # Configure API keys
uvicorn main:app --reload
```

### Mobile App

> Requires iOS Simulator, Android Emulator, or a physical device. Web target is not recommended due to platform-specific dependencies.

```bash
flutter pub get

# iOS
flutter run -d iphonesimulator

# Android
flutter run -d <android-device-id>

# macOS Desktop (macOS 11.0+)
flutter run -d macos
```

---

## License

MIT
