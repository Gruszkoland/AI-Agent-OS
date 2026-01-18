# ADRION - Getting Started Guide

> Jak szybko zacząć pracę z ADRION

---

## 🚀 5-Minutowy Quickstart

### 1. Wymagania Wstępne

```bash
# Sprawdź wersje
python --version      # Python 3.10+
docker --version      # Docker 20.10+
git --version        # Git 2.25+
```

### 2. Klonuj Repozytorium

```bash
git clone https://github.com/yourusername/AI-Agent-OS.git
cd AI-Agent-OS
```

### 3. Setup Python Environment

```bash
# Utwórz virtual environment
python -m venv venv

# Aktywuj (Linux/Mac)
source venv/bin/activate

# Aktywuj (Windows)
venv\Scripts\activate

# Zainstaluj dependencies
pip install -r requirements.txt
```

### 4. Start Database

```bash
# Uruchom PostgreSQL w Docker
docker-compose up -d postgres

# Czekaj na uruchomienie (~5s)
sleep 5

# Utwórz schemę bazy
python scripts/setup_db.py
```

### 5. Uruchom Testy

```bash
# Sprawdź czy wszystko działa
python -m pytest tests/ -v
```

**Done! ✓** Jesteś gotowy do pracy.

---

## 📚 Struktura Projektu

```
AI-Agent-OS/
│
├── 📄 README.md              ← START HERE
├── 📄 CONTRIBUTING.md        ← Jak kontrybuować
│
├── 📁 adrion/                ← Główny kod
│   ├── core/                 ← Trinity, Hexagon, Guardians
│   ├── perspectives/         ← Analiza
│   ├── modes/                ← Wykonanie
│   ├── laws/                 ← Etyka
│   └── ...
│
├── 📁 tests/                 ← Testy
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── 📁 docs/                  ← Dokumentacja
│   ├── ARCHITECTURE.md       ← Pełny opis systemu
│   ├── LOGIC.md             ← Logika matematyczna
│   └── tutorials/
│
└── 📁 scripts/              ← Skrypty pomocnicze
    ├── setup_db.py
    ├── run_tests.sh
    └── deploy.sh
```

---

## 🎯 Twoja Pierwsza Zmiana

### Scenario: "Chcę poprawić dokumentację w Trinity"

#### Krok 1: Utwórz Feature Branch

```bash
git checkout -b docs/improve-trinity-documentation
```

#### Krok 2: Zrób Zmiany

Edytuj plik:
```
adrion/core/trinity.py
```

Dodaj lepszy komentarz:
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

#### Krok 3: Testy

```bash
# Uruchom testy aby upewnić się że nic nie złamałeś
python -m pytest tests/unit/test_trinity.py -v
```

#### Krok 4: Commit

```bash
git add adrion/core/trinity.py
git commit -m "docs(trinity): improve score calculation documentation

- Add formula explanation
- Document weight distribution
- Add score interpretation guide

Helps developers understand Trinity algorithm."
```

#### Krok 5: Push i PR

```bash
# Wyślij do GitHub
git push origin docs/improve-trinity-documentation

# Przejdź na GitHub i otwórz Pull Request
# Wypełnij PR template
# Poczekaj na review
```

---

## 🔧 Wspólne Zadania

### Uruchom Konkretny Test

```bash
# Test Trinity
python -m pytest tests/unit/test_trinity.py -v

# Test Hexagon
python -m pytest tests/unit/test_hexagon.py::TestHexagon::test_mode_sequencing -v

# Wszystkie testy w folderze
python -m pytest tests/unit/ -v
```

### Sprawdź Code Quality

```bash
# Linting
flake8 adrion/ tests/

# Type checking
mypy adrion/

# Formatowanie kodu
black adrion/ tests/

# Wszystko razem
pre-commit run --all-files
```

### Uruchom Aplikację Lokalnie

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

Otwórz: http://localhost:3000

### Sprawdź Genesis Record

```bash
# Pokaż wszystkie logi
python scripts/query_genesis.py --limit 100

# Pokaż logi agenta
python scripts/query_genesis.py --agent Agent_Developer

# Weryfikuj integralność
python scripts/verify_genesis_chain.py
```

---

## 📖 Dokumentacja

### Gdzie Znaleźć Odpowiedzi

| Pytanie | Dokument |
|---------|----------|
| "Jak działa Trinity?" | [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md#3-trinity---system-trzech-perspektyw) |
| "Jaka jest Hexagon logika?" | [docs/LOGIC.md](docs/LOGIC.md#4-oś-6-tryby-wykonania) |
| "Jakie są 9 Praw?" | [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md#5-guardians---system-dziewięciu-praw) |
| "Jak kontrybuować?" | [CONTRIBUTING.md](CONTRIBUTING.md) |
| "Co jest nie tak?" | [GitHub Issues](https://github.com/yourusername/AI-Agent-OS/issues) |

### Dodaj Swoją Dokumentację

```bash
# Stwórz nowy dokument
touch docs/tutorials/how-to-create-agent.md

# Struktura
# - Wstęp (czym jest, po co)
# - Prerequisites (co trzeba)
# - Step-by-step (kroki)
# - Examples (przykłady)
# - Troubleshooting (co może być nie tak)
```

---

## 🐛 Debugging

### Zobacz Logi

```bash
# Tail aplikacji
tail -f logs/application.log

# Pokaż ostatnie 50 linii z error'em
grep ERROR logs/application.log | tail -50

# Pokaż wszystkie debug messages
grep DEBUG logs/application.log
```

### Włącz Debug Mode

```python
# W kodzie
import logging
logging.basicConfig(level=logging.DEBUG)

# Lub via environment variable
export ADRION_DEBUG=true
python -m adrion_369 --config config/development.yaml
```

### Debugowanie w IDE

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
# Uruchom z dev config
python -m adrion_369 --config config/development.yaml

# Lub z auto-reload
watchmedo auto-restart -d . -p '*.py' -- python -m adrion_369
```

### Production

```bash
# Build Docker image
docker build -t adrion369:latest .

# Uruchom container
docker-compose -f docker-compose.prod.yml up -d

# Sprawdź status
docker-compose -f docker-compose.prod.yml ps

# Logi
docker-compose -f docker-compose.prod.yml logs -f
```

### Kubernetes

```bash
# Deploy
kubectl apply -f k8s/

# Sprawdź status
kubectl get pods -n adrion

# Logi
kubectl logs -n adrion deployment/adrion-core
```

---

## 💡 Porady

### Pracuj Efektywnie

1. **Testy NAJPIERW** - Pisz test zanim kod
2. **Małe commity** - Łatwiej do review
3. **Dokumentuj jak piszesz** - Nie na końcu
4. **Pytaj wtedy gdy nie wiesz** - To OK!
5. **Review innych kodu** - Ucz się od innych

### Workspace Setup

```bash
# Zainstaluj VS Code extensions
code --install-extension ms-python.python
code --install-extension ms-python.vscode-pylance
code --install-extension eamodio.gitlens
code --install-extension ms-vscode.makefile-tools

# Zainstaluj pre-commit hooks
pre-commit install

# Setup git config
git config --local user.name "Your Name"
git config --local user.email "your@email.com"
```

---

## ❓ FAQ

### Q: Co jeśli testy mi się nie przechodzą?

A: 
```bash
# 1. Upewnij się że jesteś na main
git checkout main

# 2. Pull najnowsze zmiany
git pull origin main

# 3. Instancja dependencies
pip install -r requirements.txt

# 4. Uruchom testy
python -m pytest tests/ -v

# 5. Jeśli dalej problem - otwórz issue
```

### Q: Jaka jest maksymalna temperatura w Debate?

A: Maksymalna temperatura to **0.9** (creative mode). Predefiniowane temperatury to:
- 0.1 (conservative/paranoid)
- 0.5 (balanced/pragmatic)  
- 0.9 (creative/optimistic)

### Q: Czy mogę modyfikować 9 Praw?

A: **NIE**. Prawa są fundamentalne do systemu. Mogą być tylko reinterpretowane, nie zmieniane.

### Q: Jak długo powinny brać testy?

A: 
- Unit testy: < 1 sekunda
- Integration testy: 5-10 sekund
- E2E testy: 30+ sekund

Jeśli są wolniejsze - masz problem z wydajnością.

### Q: Czy mogę offline pracować?

A: Tak! Jedyna zależność to baza danych (PostgreSQL). Możesz pracować offline z localnym DB w Docker.

---

## 🎓 Nauka

### Zasoby

- [Sacred Geometry 369](https://en.wikipedia.org/wiki/3%E2%80%936%E2%80%939)
- [Platonic Trinity](https://www.britannica.com/topic/Platonism)
- [PAD Model Emotions](https://en.wikipedia.org/wiki/Emotion_classification#Valence%E2%80%93arousal%E2%80%93dominance)
- [Distributed Systems](https://martin.kleppmann.com/)
- [System Design](https://www.youtube.com/c/SystemDesignInterview)

### Kursy

- 📺 System Design Fundamentals
- 📚 Distributed Consensus
- 🧠 Artificial Intelligence Ethics
- 💾 Database Design at Scale

---

## 📞 Wsparcie

- **Discord**: [Community Server](https://discord.gg/adrion369)
- **GitHub**: [Issues & Discussions](https://github.com/yourusername/AI-Agent-OS)
- **Email**: contact@adrion369.ai

---

## Następne Kroki

1. ✅ Setup lokalny environment
2. ✅ Uruchom testy
3. ✅ Przeczytaj [ARCHITECTURE.md](docs/ARCHITECTURE.md)
4. ✅ Przeczytaj [CONTRIBUTING.md](CONTRIBUTING.md)
5. 🔄 Zajrzyj do [open issues](https://github.com/yourusername/AI-Agent-OS/issues)
6. 🚀 Stwórz swój pierwszy PR!

---

**Happy coding! 🎉**

Jesteś teraz gotowy by pracować nad ADRION 369.  
Dziękujemy za bycie częścią naszej misji! 🙏

---

**Last updated:** January 2026  
**Version:** 1.0-alpha
