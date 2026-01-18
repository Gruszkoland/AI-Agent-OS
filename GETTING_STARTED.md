# ADRION - Getting Started Guide

> How to quickly get started with ADRION

---

## 🚀 5-Minute Quickstart

### 1. Prerequisites

```bash
# Check versions
python --version      # Python 3.10+
docker --version      # Docker 20.10+
git --version        # Git 2.25+
```

### 2. Clone Repository

```bash
git clone https://github.com/yourusername/AI-Agent-OS.git
cd AI-Agent-OS
```

### 3. Setup Python Environment

```bash
# Create virtual environment
python -m venv venv

# Activate (Linux/Mac)
source venv/bin/activate

# Activate (Windows)
venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 4. Start Database

```bash
# Run PostgreSQL in Docker
docker-compose up -d postgres

# Wait for startup (~5s)
sleep 5

# Create database schema
python scripts/setup_db.py
```

### 5. Run Tests

```bash
# Check if everything works
python -m pytest tests/ -v
```

**Done! ✓** You're ready to work.

---

## 📚 Project Structure

```
AI-Agent-OS/
│
├── 📄 README.md              ← START HERE
├── 📄 CONTRIBUTING.md        ← How to contribute
│
├── 📁 adrion/                ← Main code
│   ├── core/                 ← Trinity, Hexagon, Guardians
│   ├── perspectives/         ← Analysis
│   ├── modes/                ← Execution
│   ├── laws/                 ← Ethics
│   └── ...
│
├── 📁 tests/                 ← Tests
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── 📁 docs/                  ← Documentation
│   ├── ARCHITECTURE.md       ← Full system description
│   ├── LOGIC.md             ← Mathematical logic
│   └── tutorials/
│
└── 📁 scripts/              ← Helper scripts
    ├── setup_db.py
    ├── run_tests.sh
    └── deploy.sh
```

---

## 🎯 Your First Change

### Scenario: "I want to improve Trinity documentation"

#### Step 1: Create Feature Branch

```bash
git checkout -b docs/improve-trinity-documentation
```

#### Step 2: Make Changes

Edit file:
```
adrion/core/trinity.py
```

Add better comment:
```python
def calculate_score(self, material: float, intellectual: float, essential: float) -> float:
    """Calculate Trinity score from three perspectives.
    
    Trinity Score represents the overall quality of decision by combining:
    - Material perspective (0.33 weight): Do we have resources?
    - Intellectual perspective (0.33 weight): Does it make sense?
    - Essential perspective (0.34 weight): Does it serve our purpose?
    
    Formula: score = (M×0.33 + I×0.33 + E×0.34) / 1.0
    
    Args:
        material: Physical/energy/information score [0, 1]
        intellectual: Truth/beauty/goodness score [0, 1]  
        essential: Unity/harmony/purpose score [0, 1]
        
    Returns:
        Trinity score [0, 1]
        - < 0.5: Not recommended
        - 0.5-0.7: Conditional approval
        - > 0.7: Recommended
    """
```

#### Step 3: Tests

```bash
# Run tests to make sure nothing broke
python -m pytest tests/unit/test_trinity.py -v
```

#### Step 4: Commit

```bash
git add adrion/core/trinity.py
git commit -m "docs(trinity): improve score calculation documentation

- Add formula explanation
- Document weight distribution
- Add score interpretation guide

Helps developers understand Trinity algorithm."
```

#### Step 5: Push and PR

```bash
# Push to GitHub
git push origin docs/improve-trinity-documentation

# Go to GitHub and open Pull Request
# Fill out PR template
# Wait for review
```

---

## 🔧 Common Tasks

### Run Specific Test

```bash
# Test Trinity
python -m pytest tests/unit/test_trinity.py -v

# Test Hexagon
python -m pytest tests/unit/test_hexagon.py::TestHexagon::test_mode_sequencing -v

# All tests in folder
python -m pytest tests/unit/ -v
```

### Check Code Quality

```bash
# Linting
flake8 adrion/ tests/

# Type checking
mypy adrion/

# Code formatting
black adrion/ tests/

# Everything together
pre-commit run --all-files
```

### Run Application Locally

```bash
# Terminal 1: Database
docker-compose up -d postgres

# Terminal 2: Backend
python -m adrion_369 --config config/development.yaml

# Terminal 3: Dashboard
cd interface/dashboard
npm install
npm run dev
```

Open: http://localhost:3000

### Check Genesis Record

```bash
# Show all logs
python scripts/query_genesis.py --limit 100

# Show agent logs
python scripts/query_genesis.py --agent Agent_Developer

# Verify integrity
python scripts/verify_genesis_chain.py
```

---

## 📖 Documentation

### Where to Find Answers

| Question | Document |
|---------|----------|
| "How does Trinity work?" | [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md#3-trinity---three-perspectives-system) |
| "What is Hexagon logic?" | [docs/LOGIC.md](docs/LOGIC.md#4-axis-6-execution-modes) |
| "What are the 9 Laws?" | [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md#5-guardians---nine-laws-system) |
| "How to contribute?" | [CONTRIBUTING.md](CONTRIBUTING.md) |
| "What's wrong?" | [GitHub Issues](https://github.com/yourusername/AI-Agent-OS/issues) |

### Add Your Documentation

```bash
# Create new document
touch docs/tutorials/how-to-create-agent.md

# Structure
# - Introduction (what it is, why)
# - Prerequisites (what's needed)
# - Step-by-step (steps)
# - Examples (examples)
# - Troubleshooting (what can go wrong)
```

---

## 🐛 Debugging

### View Logs

```bash
# Tail application
tail -f logs/application.log

# Show last 50 lines with errors
grep ERROR logs/application.log | tail -50

# Show all debug messages
grep DEBUG logs/application.log
```

### Enable Debug Mode

```python
# In code
import logging
logging.basicConfig(level=logging.DEBUG)

# Or via environment variable
export ADRION_DEBUG=true
python -m adrion_369 --config config/development.yaml
```

### Debugging in IDE

**VS Code:**
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "ADRION 369",
            "type": "python",
            "request": "launch",
            "program": "${workspaceFolder}/adrion/__main__.py",
            "console": "integratedTerminal",
            "justMyCode": true
        }
    ]
}
```

---

## 🚀 Deployment

### Development

```bash
# Run with dev config
python -m adrion_369 --config config/development.yaml

# Or with auto-reload
watchmedo auto-restart -d . -p '*.py' -- python -m adrion_369
```

### Production

```bash
# Build Docker image
docker build -t adrion369:latest .

# Run container
docker-compose -f docker-compose.prod.yml up -d

# Check status
docker-compose -f docker-compose.prod.yml ps

# Logs
docker-compose -f docker-compose.prod.yml logs -f
```

### Kubernetes

```bash
# Deploy
kubectl apply -f k8s/

# Check status
kubectl get pods -n adrion

# Logs
kubectl logs -n adrion deployment/adrion-core
```

---

## 💡 Tips

### Work Efficiently

1. **Tests FIRST** - Write test before code
2. **Small commits** - Easier to review
3. **Document as you write** - Not at the end
4. **Ask when you don't know** - It's OK!
5. **Review others' code** - Learn from others

### Workspace Setup

```bash
# Install VS Code extensions
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
code --install-extension eamodio.gitlens
code --install-extension ms-vscode.makefile-tools

# Install pre-commit hooks
pre-commit install

# Setup git config
git config --local user.name "Your Name"
git config --local user.email "your@email.com"
```

---

## ❓ FAQ

### Q: What if tests don't pass?

A: 
```bash
# 1. Make sure you're on main
git checkout main

# 2. Pull latest changes
git pull origin main

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run tests
python -m pytest tests/ -v

# 5. If still problem - open issue
```

### Q: What is the maximum temperature in Debate?

A: Maximum temperature is **0.9** (creative mode). Predefined temperatures are:
- 0.1 (conservative/paranoid)
- 0.5 (balanced/pragmatic)  
- 0.9 (creative/optimistic)

### Q: Can I modify the 9 Laws?

A: **NO**. Laws are fundamental to the system. They can only be reinterpreted, not changed.

### Q: How long should tests take?

A: 
- Unit tests: < 1 second
- Integration tests: 5-10 seconds
- E2E tests: 30+ seconds

If they're slower - you have a performance problem.

### Q: Can I work offline?

A: Yes! The only dependency is the database (PostgreSQL). You can work offline with a local DB in Docker.

---

## 🎓 Learning

### Resources

- [Sacred Geometry 369](https://en.wikipedia.org/wiki/3%E2%80%936%E2%80%939)
- [Platonic Trinity](https://www.britannica.com/topic/Platonism)
- [PAD Model Emotions](https://en.wikipedia.org/wiki/Emotion_classification#Valence%E2%80%93arousal%E2%80%93dominance)
- [Distributed Systems](https://martin.kleppmann.com/)
- [System Design](https://www.youtube.com/c/SystemDesignInterview)

### Courses

- 📺 System Design Fundamentals
- 📚 Distributed Consensus
- 🧠 Artificial Intelligence Ethics
- 💾 Database Design at Scale

---

## 📞 Support

- **Discord**: [Community Server](https://discord.gg/adrion369)
- **GitHub**: [Issues & Discussions](https://github.com/yourusername/AI-Agent-OS)
- **Email**: contact@adrion369.ai

---

## Next Steps

1. ✅ Setup local environment
2. ✅ Run tests
3. ✅ Read [ARCHITECTURE.md](docs/ARCHITECTURE.md)
4. ✅ Read [CONTRIBUTING.md](CONTRIBUTING.md)
5. 🔄 Check [open issues](https://github.com/yourusername/AI-Agent-OS/issues)
6. 🚀 Create your first PR!

---

**Happy coding! 🎉**

You're now ready to work on ADRION 369.  
Thank you for being part of our mission! 🙏

---

**Last updated:** January 2026  
**Version:** 1.0-alpha
