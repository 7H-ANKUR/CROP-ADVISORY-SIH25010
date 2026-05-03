# 🌾 Fasal.AI — Smart Crop Advisory System

**AI-powered Smart Crop Advisory System** for small & marginal farmers.  
Built for **Smart India Hackathon 2025** (Problem Statement ID: SIH25010).

> 🚀 **Live Demo**: [fasalai.app](https://fasalai.app)

---

## 🚀 Features

### 🧠 Core Intelligence

| Feature | Model / Tech | Description |
|---------|-------------|-------------|
| 🌱 **Crop Recommendation** | RandomForest (500 trees) | State-aware top-3 crop recommendations based on soil (N, P, K, pH), weather, and location |
| 🔬 **Disease Detection** | TensorFlow CNN + Gemini Vision | Upload leaf images to detect diseases — TFLite models for Potato, Corn, Rice, Sugarcane + **Gemini AI for any crop** |
| 🌾 **Yield Prediction** | GradientBoosting | Predicts crop yield (T/Ha) by state, district, crop, and season |
| 💰 **Price Forecasting** | GradientBoosting | Predicts modal mandi price (₹/Quintal) |
| 🌿 **Rotation Planner** | Rule-based engine | Dynamic season-aware crop rotation with cereal-legume rules, Gantt calendar & mobile cards |
| 🌐 **Multilingual** | Azure Translate (11 Languages) | Hindi, Tamil, Telugu, Bengali, Marathi, Kannada, Malayalam, Odia, Gujarati, Punjabi |
| 🤖 **AI Chatbot** | Gemini API | Voice-enabled agricultural assistant with speech-to-text |

### 🎯 Decision Intelligence Tools

| Feature | How it Works | Description |
|---------|-------------|-------------|
| 🔬 **What-If Simulator** | Side-by-side API comparison | Change soil/weather parameters and see how crop recommendations shift in real-time |
| 🚨 **Smart Alert Engine** | Rule-based aggregation | Combines weather, pest, and market data into prioritized, severity-coded actionable alerts |
| 💰 **Profit Planner** | Yield × Market Price – Cost | AI-powered revenue, cost, and profit estimation with multi-crop comparison |
| 📷 **Disease Scanner** | TFLite + Gemini Vision API | Unified scanner — 4 pre-trained CNN models + Gemini AI fallback for any crop worldwide |

### 🔧 Platform Features

| Feature | Tech | Description |
|---------|------|-------------|
| 👤 **Multi-User Auth** | Supabase (PostgreSQL) | Google OAuth SSO & Standard login, persistent profiles |
| 📍 **Auto Location** | Browser Geolocation + OpenWeather | Auto-detects state/city, location-aware features |
| ☀️ **Weather Dashboard** | OpenWeatherMap API | Current + 5-day forecast with farming-relevant metrics |
| ⚠️ **Pest Alerts** | Knowledge-base rules | Season-aware pest risk alerts by state |
| 📈 **Market Prices** | Agmarknet data | Real-time mandi prices with trend analysis |
| 🧪 **Fertilizer Guide** | Rule-based | Soil-aware fertilizer and remedy recommendations |
| 💬 **Community Hub** | User posts | Farmer-to-farmer discussion forum |
| 📱 **Mobile Optimized** | Tailwind CSS + React | Fully responsive with animated bottom navigation |

### 🏛️ Farmer Support

| Feature | Type | Description |
|---------|------|-------------|
| 🏛️ **Government Schemes** | Real data (10 schemes) | PM-KISAN, PMFBY, KCC, AIF, PM-KUSUM, e-NAM & more — search, filter, and apply directly to official portals |
| 🌾 **Farmer Loans** | Coming Soon teaser | 0% interest micro-loans (₹1K–₹25K) for seeds, fertilizer & farm essentials — launching soon |

---

## 🏗️ Architecture

```
SIH25010/
├── api/                       ← FastAPI backend (Python)
│   ├── main.py                # App entry, CORS, model + DB loading
│   ├── ml_service.py          # ML model loader & inference (state-aware)
│   ├── scoring_engine.py      # Constraint penalties & bonuses
│   ├── disease_service.py     # TensorFlow disease detection
│   ├── weather_service.py     # OpenWeatherMap integration
│   ├── pest_service.py        # Pest alert knowledge base
│   ├── market_service.py      # Agmarknet market data processor
│   ├── auth_service.py        # JWT auth + Google OAuth + Supabase
│   ├── profile_service.py     # User profile CRUD via Supabase
│   ├── routes.py              # All API endpoints
│   └── retrain_models.py      # Model retraining (runs on deploy)
│
├── apps/web/                  ← React + Vite frontend
│   └── src/
│       ├── index.css               # Design system (Tailwind + custom)
│       ├── App.jsx                 # Layout, sidebar, auth, routing
│       ├── contexts/
│       │   ├── AuthContext.jsx      # Auth state management
│       │   ├── LanguageContext.jsx  # i18n (11 languages)
│       │   └── LocationContext.jsx  # Geolocation auto-detect
│       ├── components/
│       │   ├── AzureTranslate.jsx  # Dynamic translation component
│       │   └── Chatbot.jsx         # Gemini AI chatbot
│       ├── services/api.js         # API client layer
│       └── pages/
│           ├── Dashboard.jsx       # Home with decision tools
│           ├── Recommend.jsx       # Crop advisory
│           ├── FieldScanner.jsx    # Unified disease detection
│           ├── WhatIfSimulator.jsx # What-if crop simulator
│           ├── SmartAlerts.jsx     # Smart alert engine
│           ├── ProfitPlanner.jsx   # Profit planner
│           ├── Planner.jsx         # Rotation planner
│           ├── Weather.jsx         # Weather dashboard
│           ├── YieldPredict.jsx    # Yield prediction
│           ├── Market.jsx          # Market prices
│           ├── PestAlerts.jsx      # Pest alerts
│           ├── Fertilizer.jsx      # Fertilizer guide
│           ├── Fields.jsx          # Field management
│           ├── Community.jsx       # Community hub
│           ├── Schemes.jsx         # Government schemes
│           ├── Loans.jsx           # Loan teaser (coming soon)
│           └── Profile.jsx         # User profile
│
├── apps/web/src/data/
│   └── schemes.json               # 10 government schemes dataset
│
├── datasets/                  ← Training datasets
├── latest_model/              ← Trained models
│   ├── *.pkl                  # ML models (auto-generated)
│   └── disease/*.h5           # CNN disease models
│
├── render.yaml                ← Render Blueprint (one-click deploy)
├── vercel.json                ← Vercel frontend config
├── Procfile                   ← Render start command
└── requirements.txt           ← Python dependencies
```

---

## ⚡ Quick Start (Local)

### Prerequisites
- Python 3.10+
- Node.js 18+

### 1. Install & Train Models
```bash
pip install -r requirements.txt
cd api
python retrain_models.py
```

### 2. Start Backend
```bash
cd api
python -m uvicorn main:app --host 0.0.0.0 --port 8000
```

### 3. Start Frontend
```bash
cd apps/web
npm install
npm run dev
```

### 4. Environment Variables
Create `apps/web/.env`:
```env
VITE_API_URL=http://localhost:8000/api
VITE_GEMINI_API_KEY=your_gemini_key
VITE_GOOGLE_CLIENT_ID=your_google_oauth_client_id
VITE_AZURE_TRANSLATOR_KEY=your_azure_translator_key
VITE_AZURE_SPEECH_KEY=your_azure_speech_key
```

Open **http://localhost:5173** → Register → Start using!

---

## 🚀 Deployment

### Backend — Render

1. Push code to GitHub
2. Go to [render.com](https://render.com) → **New → Web Service**
3. Connect your GitHub repo
4. Configure:

| Setting | Value |
|---------|-------|
| **Name** | `smartcrop-api` |
| **Region** | Oregon (or closest) |
| **Runtime** | Python |
| **Build Command** | `bash render_build.sh` |
| **Start Command** | `cd api && python -m uvicorn main:app --host 0.0.0.0 --port $PORT` |
| **Plan** | Free |

5. **Environment Variables** (Settings → Environment):

| Key | Value |
|-----|-------|
| `PYTHON_VERSION` | `3.10.12` |
| `JWT_SECRET` | *(click Generate)* |
| `SUPABASE_URL` | *(your Supabase project URL)* |
| `SUPABASE_ANON_KEY` | *(your Supabase anon key)* |

6. Click **Deploy** → Wait for build (~5-10 min)
7. Your API will be at: `https://smartcrop-api.onrender.com`

### Frontend — Vercel

1. Go to [vercel.com](https://vercel.com) → **New Project**
2. Connect your GitHub repo
3. Configure:

| Setting | Value |
|---------|-------|
| **Framework Preset** | Vite |
| **Root Directory** | `apps/web` |
| **Build Command** | `npm run build` |
| **Output Directory** | `dist` |

4. **Environment Variables**:

| Key | Value |
|-----|-------|
| `VITE_API_URL` | `https://smartcrop-api.onrender.com/api` |
| `VITE_GEMINI_API_KEY` | *(your Gemini API key)* |
| `VITE_GOOGLE_CLIENT_ID` | *(your Google OAuth client ID)* |
| `VITE_AZURE_TRANSLATOR_KEY` | *(your Azure Translator key)* |
| `VITE_AZURE_SPEECH_KEY` | *(your Azure Speech key)* |

5. Click **Deploy**

---

## 🤖 ML Models

| Model | Algorithm | Input | Output |
|-------|-----------|-------|--------|
| Crop Recommendation | RandomForest (500 trees, state-aware) | N, P, K, temp, humidity, pH, rainfall, state | Top-3 crops + confidence |
| Disease Detection | TensorFlow CNN (4 models) + Gemini Vision | Leaf image + crop type | Disease name + treatment plan |
| Yield Prediction | GradientBoosting (200 est.) | State, district, crop, season, area | Tonnes/Hectare |
| Price Prediction | GradientBoosting | State, market, commodity, price range | Modal price ₹/Quintal |

## 📡 API Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|:----:|-------------|
| `POST` | `/api/auth/register` | ❌ | Register new user |
| `POST` | `/api/auth/login` | ❌ | Login → JWT token |
| `GET` | `/api/profile` | ✅ | Get saved profile |
| `PUT` | `/api/profile` | ✅ | Update profile |
| `DELETE` | `/api/profile` | ✅ | Delete account |
| `GET` | `/api/health` | ❌ | Health check |
| `POST` | `/api/recommend/crop` | ❌ | ML crop recommendation |
| `POST` | `/api/predict/yield` | ❌ | Yield prediction |
| `POST` | `/api/predict/price` | ❌ | Price prediction |
| `GET` | `/api/weather` | ❌ | Weather data |
| `GET` | `/api/pests/alerts` | ❌ | Pest alerts |
| `GET` | `/api/market/prices` | ❌ | Market prices |
| `GET` | `/api/states` | ❌ | List of states |
| `GET` | `/api/disease/crops` | ❌ | Supported disease crops |
| `POST` | `/api/disease/detect` | ❌ | Image → disease detection |

## 🛠️ Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Backend** | FastAPI, scikit-learn, TensorFlow, pandas, Supabase (PostgreSQL), JWT |
| **Frontend** | React 19, Vite 7, Tailwind CSS, React Router, Recharts |
| **ML Models** | RandomForest, GradientBoosting, TensorFlow CNN |
| **AI Services** | Google Gemini API (chat + vision), Azure Translate, Azure Speech |
| **Auth** | Google OAuth, Standard login, JWT tokens |
| **Design** | Material 3 inspired, Manrope + Inter fonts, Emerald green theme |
| **Deployment** | Render (backend) + Vercel (frontend) |

---

## 👥 Team

Built by **ANKUR PRATAP SINGH** and team for SIH 2025.

## 📄 License

GPL-3.0 License
