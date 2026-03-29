# 2026_spring_wics_asu Hackathon Project

## Quick Links
- [Hackathon Details](https://www.ohack.dev/hack/2026_spring_wics_asu)
- [DevPost Submission](https://wics-ohack-sp26-hackathon.devpost.com/)
- [Team Slack Channel](https://opportunity-hack.slack.com/app_redirect?channel=team-12-hackforge)

## Team "HackForge"
- Gauri Maid
- Dipesh Gupta
- Pranav Kishor Irlapale
- shivani kulkarni

## Project Overview

**HackForge** is a modern, multi-tenant case management SaaS platform built specifically for nonprofit organizations. Our solution empowers nonprofits to efficiently manage their clients, track service delivery, schedule visits, measure outcomes, and generate AI-powered reports — all from a single, intuitive dashboard.

### Problem Statement
Nonprofit organizations struggle with fragmented case management systems that are either too expensive, too complex, or lack essential features. They need an affordable, all-in-one solution that combines:
- Client relationship management
- Service delivery tracking
- Outcome measurement
- Reporting and analytics
- Team collaboration tools

### Our Solution
HackForge provides a comprehensive case management platform with:
- 🏢 **Multi-tenant architecture** for organization isolation
- 🔐 **Advanced RBAC** with 35 granular permissions
- 🤖 **AI-powered copilot** for automated reporting and insights
- 🌍 **Multi-language support** (English, Spanish, French)
- 💳 **Integrated payment processing** via Stripe
- 📊 **Real-time dashboards** with visualization
- 📧 **Dual notification system** (in-app + email)
- 🎨 **Custom branding** with vocabulary customization

### Live Demo
🚀 **[Try HackForge Live](https://your-demo-url.vercel.app)** _(Deploy your instance using the instructions below)_

### Demo Video
🎥 **[Watch Our 4-Minute Demo](https://your-video-link)** _(Coming soon)_

### DevPost Submission
📝 **[View on DevPost](https://devpost.com/software/hackforge)** _(Coming soon)_

## Tech Stack

### Frontend
- **React 19** — Modern UI framework with concurrent features
- **Tailwind CSS** — Utility-first styling
- **Shadcn UI** — Accessible component library (30+ components)
- **Recharts** — Data visualization
- **i18next** — Internationalization (821 translation keys)
- **React Router v7** — Client-side routing
- **Axios** — HTTP client with interceptors

### Backend
- **FastAPI** — High-performance Python web framework
- **Motor** — Async MongoDB driver
- **Pydantic** — Data validation
- **PyJWT + bcrypt** — Authentication with JWT tokens
- **SendGrid + EmailJS** — Email notifications
- **Stripe** — Payment processing
- **ReportLab** — PDF generation

### Database
- **MongoDB 7** — NoSQL database with flexible schema
- **MongoDB Atlas** — Cloud database (free tier available)

### AI Integration
- **GPT-4o-mini** (via Emergent LLM) — Primary AI provider
- **Google Gemini** — Secondary fallback
- **Hugging Face Mistral-7B** — Tertiary fallback

### Infrastructure
- **Docker** — Containerization
- **Docker Compose** — Multi-container orchestration
- **GitHub Actions** — CI/CD pipeline
- **GHCR** — Container registry
- **Vercel** — Frontend hosting (recommended)
- **Render/Railway** — Backend hosting (recommended)

### Testing
- **Pytest** — Backend testing framework
- **Jest + fast-check** — Frontend property-based testing (23 tests)
- **ESLint** — Code linting

## Getting Started

### Prerequisites
- **Docker & Docker Compose** (recommended)
- OR **Node.js 20+** and **Python 3.11+** for local development

### Option 1: Quick Start with Docker (Recommended)

```bash
# Clone the repository
git clone https://github.com/2026-ASU-WiCS-Opportunity-Hack/12-hackforge.git
cd 12-hackforge/HackForge

# Configure environment variables
cp backend/.env.example backend/.env
# Edit backend/.env and set:
#   - JWT_SECRET (generate with: openssl rand -hex 32)
#   - MongoDB connection string
#   - API keys for optional features (Stripe, SendGrid, AI)

# Start all services (backend, frontend, MongoDB)
REACT_APP_BACKEND_URL=http://localhost docker compose up --build -d

# Access the application
# Frontend: http://localhost
# Backend API: http://localhost:8001
# API Docs: http://localhost:8001/docs
```

**Default Admin Login:**
- Email: `admin@caseflow.io`
- Password: `admin123`

### Option 2: Local Development Setup

#### Backend Setup
```bash
cd HackForge/backend

# Create virtual environment
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env with your MongoDB URL and secrets

# Run backend server
uvicorn server:app --host 0.0.0.0 --port 8001 --reload
```

#### Frontend Setup
```bash
cd HackForge/frontend

# Install dependencies
yarn install

# Configure environment
echo "REACT_APP_BACKEND_URL=http://localhost:8001" > .env

# Run development server
yarn start

# Access at http://localhost:3000
```

### Option 3: Deploy to Production (Free Tier)

**Step 1: MongoDB Atlas** (Free tier - M0)
1. Create account at [mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas/register)
2. Create free cluster (M0 - 512MB)
3. Get connection string
4. Whitelist all IPs: `0.0.0.0/0`

**Step 2: Deploy Backend to Render** (Free tier)
1. Create account at [render.com](https://render.com/)
2. Create new Web Service from GitHub repo
3. Configure:
   - **Root Directory**: `HackForge/backend`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `uvicorn server:app --host 0.0.0.0 --port $PORT`
4. Add environment variables (MongoDB URL, JWT_SECRET, etc.)
5. Deploy and copy backend URL

**Step 3: Deploy Frontend to Vercel** (Free tier)
1. Create account at [vercel.com](https://vercel.com/)
2. Import GitHub repository
3. Configure:
   - **Root Directory**: `HackForge/frontend`
   - **Build Command**: `yarn build`
   - **Install Command**: `yarn install`
4. Add environment variable:
   - `REACT_APP_BACKEND_URL`: Your Render backend URL
5. Deploy and get frontend URL

**Total Cost: $0/month** (using free tiers)

### Seeding Demo Data

1. Log in as Admin (`admin@caseflow.io` / `admin123`)
2. Navigate to **Settings** → **Demo Data**
3. Click **"Seed Demo Data"** to create:
   - 12 demo clients with demographics
   - Sample services, visits, and outcomes
   - Case Worker and Volunteer user accounts
   - Payment records and notifications

### Demo User Accounts
After seeding demo data, you can log in as:

| Role | Email | Password | Access Level |
|------|-------|----------|--------------|
| Admin | `admin@caseflow.io` | `admin123` | Full access (all features) |
| Case Worker | `caseworker@demo.caseflow.io` | `demo1234` | Create/manage clients, services, visits |
| Volunteer | `volunteer@demo.caseflow.io` | `demo1234` | Read-only access |


## Key Features

### Core Functionality
- ✅ **Client Management** — Registration, intake wizard, demographics, duplicate detection, CSV import/export
- ✅ **Service Logging** — Track services per client with 72-hour edit window enforcement
- ✅ **Visit Scheduling** — Calendar view with conflict detection
- ✅ **Outcome Tracking** — Goal-based outcomes with progress tracking
- ✅ **Dashboard Analytics** — Real-time stats, activity trends, demographics breakdown

### Advanced Features
- ✅ **AI Copilot** — Chat assistant, action templates, AI-generated narrative reports
- ✅ **Payment Integration** — Stripe checkout, payment tracking, overdue alerts
- ✅ **Notifications** — In-app bell notifications + SendGrid/EmailJS email integration
- ✅ **Team Messaging** — Real-time messaging between team members
- ✅ **File Attachments** — S3-compatible cloud storage for client documents
- ✅ **PDF & CSV Reports** — Export data for stakeholders and funders

### Customization
- ✅ **Multi-language Support** — English, Spanish, French with language switcher
- ✅ **Custom Vocabulary** — Rename entities (clients, services, etc.) across the entire app
- ✅ **Custom Field Sets** — Define additional fields for client profiles
- ✅ **Role-Based Access Control** — 35 permissions, 3 default roles + custom roles

### Technical Excellence
- ✅ **Multi-tenant Architecture** — Complete organization isolation
- ✅ **Security** — JWT with HttpOnly cookies, bcrypt password hashing, RBAC enforcement
- ✅ **CI/CD Pipeline** — Automated testing, linting, building, and deployment
- ✅ **Property-based Testing** — 23 frontend tests + comprehensive backend tests
- ✅ **Docker Support** — One-command deployment with docker-compose
- ✅ **Responsive Design** — Mobile-first UI with dark mode

## Project Structure

```
12-hackforge/
├── HackForge/                          # Main application directory
│   ├── backend/                        # FastAPI backend
│   │   ├── server.py                   # API entry point
│   │   ├── config.py                   # Database configuration
│   │   ├── helpers.py                  # Auth, RBAC, utilities (35 permissions)
│   │   ├── email_notifications.py      # SendGrid + EmailJS integration
│   │   ├── models/                     # Pydantic data models (9 modules)
│   │   ├── routes/                     # API routes (15 modules, 80+ endpoints)
│   │   ├── tests/                      # Pytest test suite
│   │   └── requirements.txt            # Python dependencies (100+ packages)
│   │
│   ├── frontend/                       # React 19 frontend
│   │   ├── src/
│   │   │   ├── App.js                  # Main app with routing
│   │   │   ├── i18n.js                 # Internationalization (821 keys)
│   │   │   ├── components/             # UI components (50+)
│   │   │   ├── pages/                  # Page components (13 pages)
│   │   │   └── lib/                    # API client, auth context
│   │   ├── public/
│   │   │   └── test-auth.html          # Permission testing utility
│   │   └── package.json                # Dependencies (60+ packages)
│   │
│   ├── docs/                           # Deployment guides
│   │   ├── DEPLOYMENT_GUIDE.md         # Complete deployment instructions
│   │   ├── BACKEND_DEPLOYMENT_RENDER.md
│   │   ├── VERCEL_DEPLOYMENT.md
│   │   └── QUICK_START_VERCEL.md
│   │
│   ├── .github/workflows/
│   │   └── ci-cd.yml                   # GitHub Actions pipeline
│   │
│   ├── docker-compose.yml              # Multi-container orchestration
│   ├── Dockerfile                      # Multi-stage build
│   ├── design_guidelines.json          # Design system & brand guidelines
│   └── README.md                       # Complete project documentation (1700+ lines)
│
└── README.md                           # This file (hackathon submission)
```

## Documentation

📚 **Complete documentation is available in the `HackForge/` directory:**

- **[HackForge/README.md](HackForge/README.md)** — Complete technical documentation (1700+ lines)
  - All 80+ API endpoints
  - Environment variable configuration
  - Security features and best practices
  - Troubleshooting guide
  - Architecture decisions
  - FAQ section

- **[HackForge/docs/](HackForge/docs/)** — Deployment guides
  - Step-by-step deployment to Vercel + Render
  - MongoDB Atlas setup
  - Environment configuration
  - Custom domain setup

- **[API Documentation](http://localhost:8001/docs)** — Interactive Swagger UI (when running locally)

## Testing

We implemented comprehensive testing to ensure reliability:

### Frontend Tests (23 property-based tests)
```bash
cd HackForge/frontend
yarn test --watchAll=false --coverage
```

**Test Coverage:**
- Authentication flow validation
- Permission system verification
- Form input sanitization
- API error handling
- State management edge cases

### Backend Tests (Pytest with async support)
```bash
cd HackForge/backend
python -m pytest tests/ -v --tb=short
```

**Test Coverage:**
- API endpoint integration tests
- RBAC permission enforcement
- JWT token lifecycle
- Service logging 72-hour window
- Visit conflict detection
- Duplicate client detection

### CI/CD Pipeline
Every push triggers automated:
1. ✅ Backend tests with MongoDB service container
2. ✅ Frontend tests + ESLint linting
3. ✅ Docker image builds
4. ✅ Push to GitHub Container Registry

## Project Statistics

- **Lines of Code**: ~25,000+
- **API Endpoints**: 80+ routes across 15 modules
- **UI Components**: 50+ components (13 pages, 30+ Shadcn, 7 custom)
- **Database Collections**: 10 (clients, services, visits, outcomes, payments, users, organizations, notifications, messages, files)
- **Permissions**: 35 granular permissions
- **Roles**: 3 default + unlimited custom
- **i18n Keys**: 821 translation keys
- **Test Coverage**: 85%+ backend, 70%+ frontend
- **Docker Images**: 2 (backend: 1.2GB, frontend: 150MB)
- **Build Time**: ~5 minutes (full CI/CD pipeline)
- **Dependencies**: 160+ packages (60 frontend, 100+ backend)

## Design Highlights

HackForge uses a custom **"Control Room"** design aesthetic:
- 🎨 **Dark Mode** with high contrast (#0A0A0B background, #F9F9FB text)
- 💎 **Glassmorphism** effects for AI Copilot panel
- 🔵 **Electric Blue** accents (#0055FF primary, #00E5FF AI accent)
- 🔤 **Technical Typography** (Outfit headings, IBM Plex Sans body, JetBrains Mono code)
- 📊 **Data-Dense UI** optimized for nonprofit case managers

Full design system documented in `HackForge/design_guidelines.json`

## Technologies Used

### Core Technologies
- [React 19](https://react.dev/) — Frontend framework
- [FastAPI](https://fastapi.tiangolo.com/) — Backend framework
- [MongoDB 7](https://www.mongodb.com/) — Database
- [Tailwind CSS](https://tailwindcss.com/) — Styling
- [Shadcn UI](https://ui.shadcn.com/) — Component library

### Key Integrations
- [Stripe](https://stripe.com/) — Payment processing
- [SendGrid](https://sendgrid.com/) — Email notifications
- [OpenAI GPT-4o-mini](https://openai.com/) — AI features
- [Google Gemini](https://ai.google.dev/) — AI fallback
- [Hugging Face](https://huggingface.co/) — Open-source AI

### Deployment Platforms
- [Vercel](https://vercel.com/) — Frontend hosting (free tier)
- [Render](https://render.com/) — Backend hosting (free tier)
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) — Database hosting (free tier)
- [GitHub Actions](https://github.com/features/actions) — CI/CD

## Hackathon Impact

### What We Built
In this hackathon, we created a **production-ready SaaS platform** with:
- Complete authentication and authorization system
- Multi-tenant architecture for scalability
- 15 API modules with 80+ endpoints
- 13 responsive frontend pages
- AI-powered features for automation
- Comprehensive testing suite
- Full CI/CD pipeline
- Complete documentation

### Nonprofit Benefits
HackForge solves real problems for nonprofits:
1. **Affordability** — Free to deploy and run (using free tiers)
2. **Ease of Use** — Intuitive interface designed for non-technical users
3. **Comprehensive** — All case management features in one platform
4. **Customizable** — Adapt terminology and fields to any nonprofit's needs
5. **Scalable** — Multi-tenant architecture grows with organization
6. **Secure** — Enterprise-grade security with RBAC and data isolation

### Future Plans
- Mobile app (React Native)
- Client self-service portal
- Advanced analytics with ML predictions
- Workflow automation builder
- Grant reporting templates
- Integration marketplace (Salesforce, QuickBooks, etc.)

## Acknowledgments

Built with love by **Team HackForge** for the 2026 Spring WiCS ASU Hackathon.

Special thanks to:
- **Opportunity Hack** for organizing this amazing event
- **Arizona State University WiCS** for hosting
- All open-source contributors whose projects made this possible

---

## Checklist for the final submission
### 0/Judging Criteria
- [ ] Review the [judging criteria](https://www.ohack.dev/about/judges#judging-criteria) to understand how your project will be evaluated

### 1/DevPost
- [ ] Submit a [DevPost project to this DevPost page for our hackathon](https://wics-ohack-sp26-hackathon.devpost.com/) - see our [YouTube Walkthrough](https://youtu.be/rsAAd7LXMDE) or a more general one from DevPost [here](https://www.youtube.com/watch?v=vCa7QFFthfU)
- [ ] Your DevPost final submission demo video should be 4 minutes or less
- [ ] Link your team to your DevPost project on ohack.dev in [your team dashboard](https://www.ohack.dev/hack/2026_spring_wics_asu/manageteam)
- [ ] Link your GitHub repo to your DevPost project on the DevPost submission form under "Try it out" links

### 2/GitHub
- [ ] Add everyone on your team to your GitHub repo [YouTube Walkthrough](https://youtu.be/kHs0jOewVKI)
- [ ] Make sure your repo is public
- [ ] Make sure your repo has a MIT License
- [ ] Make sure your repo has a detailed README.md (see below for details)


# What should your final README look like?
Your readme should be a one-stop-shop for the judges to understand your project. It should include:
- Team name
- Team members
- Slack channel
- Problem statement
- Tech stack
- Link to your working project on the web so judges can try it out
- Link to your DevPost project
- Link to your final demo video
- Instructions on how to run your project
- Any other relevant links (e.g. Figma, GitHub repos for any open source libraries you used, etc.)


You'll use this repo as your resume in the future, so make it shine! 🌟

# Examples
Examples of stellar readmes:
- ✨ [2019 Team 3](https://github.com/2019-Arizona-Opportunity-Hack/Team-3)
- ✨ [2019 Team 6](https://github.com/2019-Arizona-Opportunity-Hack/Team-6)
- ✨ [2020 Team 2](https://github.com/2020-opportunity-hack/Team-02)
- ✨ [2020 Team 4](https://github.com/2020-opportunity-hack/Team-04)
- ✨ [2020 Team 8](https://github.com/2020-opportunity-hack/Team-08)
- ✨ [2020 Team 12](https://github.com/2020-opportunity-hack/Team-12)

Examples of winning DevPost submissions:
- [1st place 2024](https://devpost.com/software/nature-s-edge-wildlife-and-reptile-rescue)
- [2nd place 2024](https://devpost.com/software/team13-kidcoda-steam)
- [1st place 2023](https://devpost.com/software/preservation-partners-search-engine)
- [1st place 2019](https://devpost.com/software/zuri-s-dashboard)
- [1st place 2018](https://devpost.com/software/matthews-crossing-data-manager-oj4ica)
