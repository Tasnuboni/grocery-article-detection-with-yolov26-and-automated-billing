# Grocery Article Detection with YOLOv26 and Automated Billing

Real-time grocery item detection via webcam using a YOLOv26 model, with automatic billing and printable receipt generation.

**Live Demo:** [grocery-article-detection-with-yolo.vercel.app](https://grocery-article-detection-with-yolo.vercel.app)

---

## Prerequisites

Before starting, make sure you have the following installed:

- [Python 3.10+](https://www.python.org/downloads/)
- [Node.js 18+](https://nodejs.org/)
- `model.pt` — included in the repo inside the `backend/` folder

---

## Backend Setup

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload
```

The API will be available at `http://localhost:8000`.

---

## Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

The app will be available at `http://localhost:3000`.

---

## How to Use

1. Open `http://localhost:3000` in your browser
2. Click **Start Camera** — activates your webcam
3. Click **Start Detect** — begins real-time YOLO inference (~8 fps)
4. Hold grocery items in front of the camera
5. Click **Stop Detect** — stops inference and generates the bill automatically
6. Click **View Receipt** then **Print Receipt** to print

> Objects must be visible for more than 3 frames with confidence above 75% to be added to the bill.

---

## Tech Stack

| Layer    | Technology                          |
|----------|-------------------------------------|
| Model    | YOLOv26 (Ultralytics)               |
| Backend  | Python, FastAPI, Uvicorn            |
| Frontend | Next.js 14, TypeScript, Tailwind CSS |

---

## Project Structure

```
├── backend/
│   ├── main.py          # FastAPI app
│   ├── detector.py      # YOLO inference logic
│   ├── prices.json      # Item prices
│   ├── model.pt         # Trained YOLOv26 model
│   ├── Dockerfile       # Railway deployment
│   ├── railway.toml     # Railway config
│   └── requirements.txt
└── frontend/
    ├── app/             # Next.js pages
    ├── components/      # Camera, CartPanel, Receipt
    ├── hooks/           # useCamera, useDetection
    └── types/           # TypeScript types
```
