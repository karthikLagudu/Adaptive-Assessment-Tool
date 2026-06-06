# Adaptive Assessment Tool

A robust, full-stack application serving as a diagnostic engine for NCERT-aligned mathematics. This platform leverages advanced psychometric and machine learning models, including Computerized Adaptive Testing (CAT), Item Response Theory (IRT), Cognitive Diagnostic Modeling (CDM), Bayesian Knowledge Tracing (BKT), and Deep Knowledge Tracing (DKT), to provide a tailored assessment experience.

## 🚀 Features

* **Advanced Diagnostic Engine**: Utilizes CAT/IRT, CDM, BKT, and DKT models to dynamically adapt questions and trace student knowledge.
* **Admin Dashboard**: Built-in administration interface with auto-seeding of default credentials upon initialization.
* **RESTful API**: Fast, asynchronous backend powered by FastAPI.
* **Modern Frontend**: Responsive, component-driven UI built with Next.js 14, React 18, and TailwindCSS.
* **Data Visualization**: Interactive assessment metrics and charts using Recharts.
* **Production-Ready**: Pre-configured for deployment on Render with PostgreSQL integration.

## 🛠️ Tech Stack

### Frontend
* **Framework**: Next.js (v14.2.35) & React 18
* **Styling**: TailwindCSS
* **Charts/Visuals**: Recharts
* **Icons**: Lucide-React
* **HTTP Client**: Axios

### Backend
* **Framework**: FastAPI with Uvicorn
* **Database ORM**: SQLAlchemy
* **Data Processing & Math**: Pandas, NumPy, SciPy
* **Authentication**: Passlib (bcrypt), python-jose
* **Database**: PostgreSQL (via psycopg2-binary)

### Infrastructure
* **Deployment**: Render (Configured via `render.yaml`)
* **Database**: Render PostgreSQL

## 📂 Project Structure

.
├── backend/                # FastAPI Python application
│   ├── app/
│   │   ├── main.py         # Application entry point & router inclusion
│   │   ├── database.py     # SQLAlchemy DB configuration
│   │   ├── models.py       # Database models (e.g., AdminUser)
│   │   └── routers/        # API route handlers (session, admin)
│   └── requirements.txt    # Python dependencies
├── frontend/               # Next.js React application
│   ├── package.json        # Node.js dependencies & scripts
│   └── ...                 # React components and Next.js pages
└── render.yaml             # Render infrastructure-as-code configuration


## 💻 Local Development Setup

### Prerequisites
* Node.js (v18 or higher)
* Python (v3.11.0 recommended)
* PostgreSQL

### 1. Backend Setup

1. Navigate to the backend directory:
   cd backend
   
2. Create and activate a virtual environment:
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scriptsctivate`
   
3. Install the dependencies:
   pip install -r requirements.txt
   
4. Set your environment variables (create a `.env` file):
   DATABASE_URL=postgresql://user:password@localhost/symphony
   FRONTEND_URL=http://localhost:3000
   ADMIN_DEFAULT_PASSWORD=admin123
   
5. Run the FastAPI development server:
   uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
   
   *Note: On the first run, the system will automatically create the database tables and seed the default admin user (Username: admin).*

### 2. Frontend Setup

1. Navigate to the frontend directory:
   cd frontend
   
2. Install the required NPM packages:
   npm install
   
3. Set your environment variables (create a `.env.local` file):
   NEXT_PUBLIC_API_URL=http://localhost:8000
   
4. Start the Next.js development server:
   npm run dev
   

The frontend will be accessible at http://localhost:3000 and the API documentation (Swagger UI) at http://localhost:8000/docs.

## ☁️ Deployment

This project is configured for seamless deployment on **Render** using the included `render.yaml` file. 

The configuration provisions three services:
1. **symphony-db**: A PostgreSQL database instance.
2. **symphony-backend**: A Python web service running the FastAPI application.
3. **symphony-frontend**: A Node web service running the Next.js frontend, pre-linked to the backend API endpoint.
