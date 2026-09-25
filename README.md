# FairLens AI — Bias Detection & Mitigation Platform

FairLens AI is a hackathon-level MVP designed to detect, explain, and mitigate bias in datasets and machine learning models. Built for HR teams, banks, and healthcare analysts to ensure fairness and compliance.

## 📂 Folder Structure

```
FairLens/
│
├── backend/                  # FastAPI Backend
│   ├── main.py               # Core API & ML Fairness Module
│   └── requirements.txt      # Python dependencies
│
└── frontend/                 # React.js Frontend
    ├── public/
    ├── src/
    │   ├── App.jsx           # Main UI & State Management
    │   ├── index.css         # Tailwind CSS & custom styling
    │   └── main.jsx          # React Entry
    ├── package.json          # Node dependencies
    ├── tailwind.config.js    # Tailwind Config
    └── postcss.config.js     # PostCSS Config
```

## 🛠️ Setup Instructions

### 1. Backend Setup (FastAPI)
Open a terminal and navigate to the `backend` folder:
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```
The backend will run on `http://localhost:8000`.

### 2. Frontend Setup (React)
Open another terminal and navigate to the `frontend` folder:
```bash
cd frontend
npm install
npm run dev
```
The frontend will run on `http://localhost:5173`.

---

## 🔬 ML Fairness Module (Core Logic)
The core ML logic is located in `backend/main.py`. It uses:
- **Fairlearn:** For calculating metrics like `demographic_parity_difference` and `disparate_impact_ratio`.
- **CorrelationRemover:** A pre-processing technique to remove the correlation between sensitive features and the rest of the dataset.

---

## 📡 Sample API Responses

**`POST /analyze`**
```json
{
  "metrics": {
    "demographic_parity_difference": 0.21,
    "disparate_impact_ratio": 0.58,
    "bias_score": 58.0,
    "risk_level": "High"
  },
  "distribution": {
    "Male": { "count": 500, "favorable_count": 250, "approval_rate": 0.5 },
    "Female": { "count": 500, "favorable_count": 145, "approval_rate": 0.29 }
  },
  "explanation": "Analyzed outcomes across 'Gender'. Group 'Female' is 21.0% less likely to receive the favorable outcome compared to group 'Male'."
}
```

**`POST /mitigate`**
```json
{
  "before": {
    "accuracy": 0.84,
    "demographic_parity_difference": 0.18
  },
  "after": {
    "accuracy": 0.82,
    "demographic_parity_difference": 0.04
  },
  "technique": "CorrelationRemover"
}
```

---

## 🚀 Deployment Guide

### Backend on Render
1. Push your code to GitHub.
2. Go to [Render](https://render.com/) and create a new **Web Service**.
3. Connect your repository.
4. Set the Root Directory to `backend`.
5. Build Command: `pip install -r requirements.txt`
6. Start Command: `uvicorn main:app --host 0.0.0.0 --port 10000`
7. Deploy.

### Frontend on Vercel
1. Go to [Vercel](https://vercel.com/) and create a new Project.
2. Import the GitHub repository.
3. Set the Root Directory to `frontend`.
4. Add an Environment Variable: `VITE_API_URL` pointing to your Render backend URL (if you change `API_URL` in `App.jsx` to `import.meta.env.VITE_API_URL`).
5. Click **Deploy**.

## 🎥 Demonstration Script
* **Intro (0:00-0:15):** "Meet FairLens AI, the platform ensuring fairness in your AI systems. Today we're analyzing a loan approval dataset."
* **Detection (0:15-0:30):** "We upload the data and instantly detect a 21% disparity in approvals between genders. FairLens explains this in plain English and flags it as High Risk."
* **Mitigation (0:30-0:45):** "With one click, we train a debiased model. The platform applies Correlation Removal, dropping the bias by 75% while maintaining 82% accuracy."
* **Outro (0:45-1:00):** "FairLens AI: Making AI fair, accountable, and transparent..."
