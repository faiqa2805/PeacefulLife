# 🏠 Hostel Room Allocation System

A smart hostel room allocation system that aims to improve roommate compatibility using personality-based grouping and feedback-driven improvement.

## 🎯 Problem

Hostel room allocation is often performed randomly or using basic administrative constraints.

This can result in incompatible roommate combinations and reduced student satisfaction.

Our system explores a personality-based approach where students complete a personality questionnaire during hostel admission. Their personality characteristics are converted into numerical representations and used to generate compatible roommate groups.

Student feedback after living together is stored as historical data, creating the foundation for improving the allocation system over time.

---

## 🚀 MVP Goal

The first version of the project will provide:

* Student registration
* Personality questionnaire
* Personality/MBTI classification
* Room and hostel management
* Personality-based student grouping
* Automatic room allocation
* Admin review of generated allocations
* Roommate satisfaction feedback
* Storage of historical feedback for future model improvement

---

## 🧠 Initial Allocation Approach

The MVP will use a personality-based compatibility approach rather than a fully trained machine-learning model.

The initial pipeline is:

```text
Personality Questionnaire
        ↓
Personality / MBTI Type
        ↓
Numerical Feature Representation
        ↓
Vector Similarity / Distance
        ↓
Compatibility Score
        ↓
Student Grouping
        ↓
Room Allocation
```

The feedback collected after allocation will be used as historical data for evaluating and improving future versions of the model.

> Note: MBTI is being used as an initial experimental personality representation. Future versions may incorporate more behaviorally relevant personality features and additional student preferences.

---

## 🏗️ System Architecture

```text
                 ┌─────────────────────┐
                 │    React Frontend   │
                 │                     │
                 │ Student + Admin UI  │
                 └──────────┬──────────┘
                            │
                         REST API
                            │
                            ▼
                 ┌─────────────────────┐
                 │   Node.js Backend   │
                 │      Express        │
                 │                     │
                 │ Students            │
                 │ Rooms               │
                 │ Allocation          │
                 │ Feedback            │
                 └───────┬───────┬─────┘
                         │       │
                         │       ▼
                         │   Database
                         │
                         ▼
                 ┌─────────────────────┐
                 │  Python FastAPI     │
                 │    ML Service       │
                 │                     │
                 │ Feature generation  │
                 │ Similarity          │
                 │ Grouping             │
                 └─────────────────────┘
```

---

## 📁 Project Structure

```text
hostel-room-allocation/
│
├── frontend/
│   └── React application
│
├── backend/
│   └── Node.js + Express API
│
├── ml-service/
│   └── Python + FastAPI service
│
├── database/
│   ├── schema/
│   └── seed/
│
├── docs/
│   ├── architecture.md
│   ├── api.md
│   └── ml-approach.md
│
├── .gitignore
└── README.md
```

---

## 🛠️ Tech Stack

### Frontend

* React
* JavaScript
* HTML/CSS

### Backend

* Node.js
* Express.js
* REST APIs

### ML Service

* Python
* FastAPI
* NumPy
* scikit-learn

### Database

The database technology will be finalized during the initial setup.

---

## 👥 Team Responsibilities

| Member   | Responsibility                    |
| -------- | --------------------------------- |
| Member 1 | Node.js backend + API integration |
| Member 2 | ML / compatibility algorithm      |
| Member 3 | React frontend                    |
| Member 4 | ML/data pipeline + evaluation     |

Responsibilities may overlap as the project develops.

---

## 🔌 Initial API Plan

### Students

```text
POST   /api/students
GET    /api/students
GET    /api/students/:id
PUT    /api/students/:id
DELETE /api/students/:id
```

### Personality

```text
POST /api/students/:id/personality
GET  /api/students/:id/personality
```

### Rooms

```text
POST /api/rooms
GET  /api/rooms
GET  /api/rooms/:id
```

### Allocation

```text
POST /api/allocation/generate
GET  /api/allocation
GET  /api/students/:id/r
oom
```

### Feedback

```text
POST /api/feedback
GET  /api/feedback
```

---

## 🔄 Development Workflow

We use a feature-branch workflow.

Create a branch:

```bash
git checkout -b feature/your-feature
```

After making changes:

```bash
git add .
git commit -m "feat: describe your change"
git push origin feature/your-feature

```

Create a Pull Request to:

```text
develop
```

Do not directly push feature work to `main`.

---

## ⚙️ Local Setup

### 1. Clone the repository

```bash
git clone <REPOSITORY_URL>
cd hostel-room-allocation
```

### 2. Frontend

```bash
cd frontend
npm install
npm run dev
```

### 3. Backend

Open another terminal:

```bash
cd backend
npm install
npm run dev
```

### 4. ML Service

Open another terminal:

```bash
cd ml-service

python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run:

```bash
uvicorn app.main:app --reload
```

---

## 📊 Future Development

The project is planned in stages.

### Phase 1 — MVP

* Student management
* Personality questionnaire
* Personality representation
* Compatibility calculation
* Room grouping
* Room allocation
* Feedback collection

### Phase 2 — Better Compatibility

Introduce additional factors such as:

* Sleep schedule
* Study habits
* Cleanliness preferences
* Noise tolerance
* Food preferences
* Social preferences
* Smoking/non-smoking preferences
* Room preferences

### Phase 3 — Feedback-Based Model

Historical data:

```text
Student characteristics
+
Roommate characteristics
+
Allocation
+
Satisfaction feedback
```

can be used to evaluate and train improved compatibility models.

### Phase 4 — Production Features

* Authentication
* Multiple hostel blocks
* Admission rounds
* Waiting lists
* Room transfer requests
* Admin approval
* Allocation constraints
* Analytics
* Model evaluation dashboard

---

## ⚠️ Important Considerations

The system should not make irreversible allocation decisions automatically.

The recommended workflow is:

```text
ML-generated allocation
        ↓
Admin review
        ↓
Final allocation
```

The system should also account for hard constraints such as hostel rules, room capacity, gender/eligibility restrictions, accessibility requirements, and other institutional policies before applying personality-based optimization.

---

## 📌 Current Status

**Project:** Hostel Room Allocation System

**Stage:** MVP Development

**Primary Goal:** Build a working prototype demonstrating personality-based roommate grouping and feedback collection.

---

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
