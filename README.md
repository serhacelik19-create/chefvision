# ChefVision AI - Smart Recipe Advisor

> [!NOTE]
> **Status: Active Development** — This project is currently in active development. Features are continuously being updated, refactored, and improved.

ChefVision AI is a smart recipe advisor and ingredient recognition system powered by advanced AI and computer vision. It allows users to scan kitchen ingredients using their camera, receive personalized recipe recommendations, and interact with an integrated voice assistant for hands-free cooking guidance.

This repository is a sanitized public demo of the project, showcasing frontend layout, backend APIs, data structures, and mobile app flows for portfolio review, while keeping private API keys and database credentials safe.

## What The Project Shows

- **AI-Powered Ingredient Scanning**: Mobile client camera workflow that detects raw ingredients using Gemini AI.
- **Voice-Assisted Cooking**: Hands-free instruction reading and interactive speech commands during food preparation.
- **Robust Caching & Queueing**: Python (FastAPI) backend using Redis for response caching and fast lookup.

## Repository Structure

Inside this folder, you will find:
- **`lib/`**, **`android/`**, **`ios/`**: The core Flutter mobile application code.
- **`backend/`**: Python FastAPI backend supporting authentication, recipe pipelines, database ORM, and Gemini API connectors.

## Tech Stack

- **Mobile Client**: Flutter, Dart, Camera API, local storage, Speech-to-Text & Text-to-Speech integration.
- **Backend API**: Python, FastAPI, SQLAlchemy, PostgreSQL, Redis, Firebase Admin SDK.

## Demo & Security Safeguards

- No `.env` files are included.
- No live database passwords, Gemini AI API keys, or Firebase keys are committed.
- Speech engines and Gemini client endpoints are configured with developer placeholders.
- Database runs locally using standard configurations.

## Setup & Running Instructions

### 1. Python Backend

The backend requires **PostgreSQL** and **Redis**. A docker-compose file is provided to start these services locally.

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Start the local database and redis containers:
   ```bash
   docker-compose up -d
   ```

3. Create and activate a Python virtual environment (recommended Python 3.11 or 3.12):
   ```bash
   python3.11 -m venv venv
   source venv/bin/activate
   ```

4. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

5. Configure your environment variables in `.env` (copied from `.env.example`).

6. Start the FastAPI development server:
   ```bash
   uvicorn main:app --reload
   ```

### 2. Flutter Mobile App

The mobile app should be tested on **iOS Simulator**, **Android Emulator**, or a physical device (web/Chrome target is not recommended due to Apple StoreKit platform dependencies).

1. Install dependencies from the project root:
   ```bash
   flutter pub get
   ```

2. Run the application:
   - For iOS Simulator:
     ```bash
     flutter run -d iphonesimulator
     ```
   - For Android Emulator:
     ```bash
     flutter run -d <android-device-id>
     ```
   - For macOS desktop application (requires macOS 11.0+):
     ```bash
     flutter run -d macos
     ```
