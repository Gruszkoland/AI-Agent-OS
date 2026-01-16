# Contributing to ADRION 369

Dziękujemy za zainteresowanie udziałem w projekcie ADRION 369! 🙏

---

## 📋 Spis Treści

- [Code of Conduct](#code-of-conduct)
- [Jak Zacząć](#jak-zacząć)
- [Proces Kontrybutora](#proces-kontrybutora)
- [Wytyczne Kodowania](#wytyczne-kodowania)
- [Struktura Commitów](#struktura-commitów)
- [Proces PR](#proces-pr)
- [Testy](#testy)
- [Dokumentacja](#dokumentacja)
- [Getting Help](#getting-help)

---

## Code of Conduct

### Nasze Zasady

Projekt ADRION 369 jest zbudowany na **9 Prawach Etycznych**. Oczekujemy od wszystkich kontrybutorów respektowania tych zasad:

#### 🤝 **Prawo 1: Unity - Jedność**
- Działaj dla wspólnego dobra, nie dla osobistych korzyści
- Wspieraj inne osoby w zespole
- Dziel się wiedzą i doświadczeniem
- Rozwiązuj konflikty konstruktywnie

#### 🧠 **Prawo 2: Truth - Prawda**
- Bądź szczery w komunikacji i codzie
- Przyznaj błędy i ucz się z nich
- Weryfikuj informacje zanim je upubliczniasz
- Nie manipuluj czy nie kłam

#### ⏰ **Prawo 3: Rhythm - Rytm**
- Pracuj w zdrowych cyklach (nie workoholizm)
- Szanuj czas innych ludzi
- Respond w rozsądnym czasie (24-48h)
- Robienie przerwę jest OK i zachęcane

#### ➡️ **Prawo 4: Causality - Przyczynowość**
- Dokumentuj DLACZEGO, nie tylko CO
- Wyjaśnij swoją logikę w PR/commitach
- Bądź odpowiedzialny za swój kod
- Śledź konsekwencje zmian

#### 👀 **Prawo 5: Transparency - Przejrzystość**
- Komunikuj jasno i otwarcie
- Bądź dostępny dla pytań i reviewu
- Nie ukrywaj problemów - mów o nich wcześnie
- Dziel się decyzjami i ich uzasadnieniami

#### 🛡️ **Prawo 6: Nonmaleficence - Nieszkodzenie**
- Nie złamyj istniejącego kodu bez powodu
- Testuj przed push
- Komunikuj breaking changes
- Minimalizuj ryzyko dla produkcji

#### 🗳️ **Prawo 7: Autonomy - Autonomia**
- Szanuj decyzje inne osób
- Nie wymuszaj swoich pomysłów
- Zaakceptuj konstruktywną krytykę
- Pozwól innym wybrać własną ścieżkę

#### ⚖️ **Prawo 8: Justice - Sprawiedliwość**
- Zwracaj uwagę osobom niedoreprezentowanym
- Nie dyskryminuj
- Daj równą szansę wszystkim
- Będz fair w ocenie wkładu

#### 🌱 **Prawo 9: Sustainability - Zrównoważenie**
- Pisz kod, który będzie zrozumiały za 2 lata
- Inwestuj w long-term (nie hack'i)
- Dbaj o technical debt
- Pomyśl o przyszłości projektu

### Konsekwencje Naruszenia

Naruszenie tego Code of Conduct może prowadzić do:
- Uwagi (pierwszy raz)
- Warningów (powtórzenie)
- Tymczasowego zawieszenia (poważne naruszenia)
- Permanentnego zbanowania (powtarzające się naruszenia)

---

## Jak Zacząć

### 1. Ustaw Środowisko

```bash
# Klonuj repozytorium
git clone https://github.com/yourusername/AI-Agent-OS.git
cd AI-Agent-OS

# Utwórz virtual environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
# lub
venv\Scripts\activate  # Windows

# Zainstaluj dependencies
pip install -r requirements.txt
pip install -r requirements-dev.txt

# Zainstaluj pre-commit hooks
pre-commit install
```

### 2. Utwórz Branch

```bash
git checkout -b feature/your-feature-name
```

### 3. Rozpocznij Pracę

```bash
# Upewnij się że testy przechodzą
python -m pytest tests/

# Sprawdź linting
flake8 adrion/ tests/
black --check adrion/ tests/
mypy adrion/

# Formatuj kod
black adrion/ tests/
```

---

## Proces Kontrybutora

### Kroki:

1. **Fork** repozytorium
2. **Clone** swój fork
3. **Create** feature branch (`git checkout -b feature/amazing-feature`)
4. **Make** zmiany
5. **Test** twój kod
6. **Commit** zmiany (`git commit -m 'Add amazing feature'`)
7. **Push** do branch (`git push origin feature/amazing-feature`)
8. **Open** Pull Request
9. **Respond** na review comments
10. **Merge** (gdy approved)

### Diagram:

```
Your Fork (origin)
      ↓
  feature/amazing-feature
      ↓
   Commit & Push
      ↓
  Create PR
      ↓
  Code Review
      ↓
  Respond to feedback
      ↓
  Approved? YES
      ↓
  Merge to Main
```

---

## Wytyczne Kodowania

### Python Style

Postępuj zgodnie z **PEP 8** i **Google Python Style Guide**:

```python
# ✓ DOBRY KOD

def analyze_perspective(request: Request, timeout: int = 5000) -> AnalysisResult:
    """Analyze request through three perspectives.
    
    Args:
        request: User request to analyze
        timeout: Maximum execution time in ms
        
    Returns:
        AnalysisResult with Trinity score
        
    Raises:
        TimeoutError: If analysis exceeds timeout
    """
    try:
        material = _analyze_material(request, timeout // 3)
        intellectual = _analyze_intellectual(request, timeout // 3)
        essential = _analyze_essential(request, timeout // 3)
        
        score = _calculate_trinity_score(material, intellectual, essential)
        return AnalysisResult(score=score, components=(material, intellectual, essential))
    except TimeoutError as e:
        logger.error(f"Analysis timeout: {e}")
        raise


# ✗ ZŁY KOD

def analyze(r, t=5000):
    """Analyze."""
    m = analyze_mat(r, t)
    i = analyze_int(r, t)
    e = analyze_ess(r, t)
    s = (m + i + e) / 3
    return s
```

### Type Hints

Zawsze używaj type hints:

```python
# ✓ DOBRY KOD
def process_task(task_id: str, agent: Agent) -> Task:
    """Process a task."""
    pass

# ✗ ZŁY KOD
def process_task(task_id, agent):
    """Process a task."""
    pass
```

### Dokumentacja

Każda funkcja musi mieć **docstring**:

```python
def calculate_temperature(arousal: float, pleasure: float) -> float:
    """Calculate decision temperature based on emotional state.
    
    Formula: temperature = max(0.1, 1.0 - (arousal × (1 - pleasure)))
    
    Args:
        arousal: Level of agent activation [0, 1]
        pleasure: Emotional valence [-1, 1]
        
    Returns:
        Decision temperature [0.1, 1.0]
        - 0.1-0.3: Conservative mode (paranoid)
        - 0.3-0.7: Normal mode (balanced)
        - 0.7-1.0: Exploration mode (creative)
        
    Example:
        >>> calculate_temperature(arousal=0.4, pleasure=0.6)
        0.72
        
    Note:
        This implements the PAD model emotional regulation.
    """
    stress = arousal * (1 - pleasure)
    return max(0.1, 1.0 - stress)
```

### Nazewnictwo

```python
# ✓ DOBRY KOD - jasne i opisowe
class TrinityScoringEngine:
    def calculate_material_score(self, analysis: MaterialAnalysis) -> float:
        pass

# ✗ ZŁY KOD - niejasne
class TSE:
    def calc_m_s(self, a):
        pass
```

### Struktura Kodu

```
adrion/
├── core/
│   ├── trinity.py          # Trinity analyzer
│   ├── hexagon.py          # Hexagon orchestrator
│   ├── guardians.py        # Guardian verifier
│   └── ebdi_model.py       # Emotional model
├── perspectives/
│   ├── material/
│   ├── intellectual/
│   └── essential/
├── modes/
│   ├── inventory/
│   ├── empathy/
│   └── ...
├── utils/
│   ├── logging.py
│   └── validators.py
└── __init__.py
```

---

## Struktura Commitów

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat`: Nowa funkcjonalność
- `fix`: Poprawka bugu
- `docs`: Zmiany dokumentacji
- `style`: Formatowanie kodu (bez logiki)
- `refactor`: Refaktoryzacja kodu
- `perf`: Poprawy performance
- `test`: Dodanie/modyfikacja testów
- `chore`: Zmiany toolingu, dependencies

### Przykłady

```bash
# ✓ DOBRY COMMIT
git commit -m "feat(trinity): add material perspective analyzer

- Implement physical_analyzer for CPU/RAM metrics
- Implement energy_analyzer for power consumption
- Implement information_analyzer for data quality
- Add integration tests

Fixes #123"

# ✗ ZŁY COMMIT
git commit -m "fix stuff"
git commit -m "WIP: random changes"
```

---

## Proces PR

### Przed Wysłaniem

1. **Rebase** na najnowsze `main`
2. **Testy** przechodzą lokalnie
3. **Linting** przechodzą
4. **Documentation** zaktualizowana
5. **Changelog** zaktualizowany

### Checklist PR

```markdown
## Description
What does this PR do?

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## How to Test
Steps to verify changes:
1. ...
2. ...

## Checklist
- [ ] Testy napisane i przechodzą
- [ ] Kod poddany lintingowi
- [ ] Dokumentacja zaktualizowana
- [ ] Nie wprowadzam breaking changes (jeśli nie celowo)
- [ ] Commit messages są czyste
- [ ] CHANGELOG.md zaktualizowany

## Related Issues
Fixes #123
Related to #456
```

### Code Review

Gdy ktoś da Ci review comments:

1. **Czytaj uważnie** - starają się Ci pomóc
2. **Odpowiadaj uprzejmie** - wyjaśniaj swoje podejście
3. **Implementuj** - wprowadź zmiany szybko
4. **Re-request review** - gdy skończyłeś
5. **Dziękuj** - wszyscy pracujemy dla wspólnego dobra

---

## Testy

### Wymagania

- Minimum 80% code coverage
- Wszystkie testy muszą przechodzić
- Nowe funkcje = nowe testy

### Struktura

```
tests/
├── unit/                    # Testowanie funkcji/metod
│   ├── test_trinity.py
│   ├── test_hexagon.py
│   └── test_perspectives.py
├── integration/            # Testowanie komunikacji
│   ├── test_system_flow.py
│   └── test_agent_coordination.py
└── e2e/                   # End-to-end scenariusze
    ├── test_complete_request.py
    └── test_emotional_regulation.py
```

### Pisanie Testów

```python
import pytest
from adrion.core import Trinity
from adrion.perspectives import MaterialAnalyzer

class TestTrinity:
    """Test Trinity scoring engine."""
    
    @pytest.fixture
    def trinity(self):
        """Setup Trinity instance."""
        return Trinity()
    
    def test_trinity_score_calculation(self, trinity):
        """Test that Trinity correctly calculates score."""
        # Arrange
        material_score = 0.8
        intellectual_score = 0.9
        essential_score = 0.85
        
        # Act
        score = trinity.calculate_score(material_score, intellectual_score, essential_score)
        
        # Assert
        assert score == pytest.approx(0.85)
        assert 0 <= score <= 1
    
    def test_trinity_detects_imbalance(self, trinity):
        """Test that Trinity detects imbalanced perspectives."""
        # Arrange
        material_score = 0.2      # Very low
        intellectual_score = 0.9
        essential_score = 0.85
        
        # Act
        balance = trinity.calculate_balance(material_score, intellectual_score, essential_score)
        
        # Assert
        assert balance > 0.3  # Should be imbalanced
```

### Uruchomienie Testów

```bash
# Uruchom wszystkie testy
python -m pytest

# Uruchom testy z coverage
python -m pytest --cov=adrion tests/

# Uruchom konkretny test
python -m pytest tests/unit/test_trinity.py::TestTrinity::test_trinity_score_calculation

# Uruchom z verbose output
python -m pytest -v

# Uruchom tylko testy integracyjne
python -m pytest tests/integration/
```

---

## Dokumentacja

### Gdzie Dokumentować

1. **Code comments** - DLACZEGO, nie CO (kod pokazuje CO)
2. **Docstrings** - Każda funkcja/klasa
3. **README** - Ogólny wstęp
4. **docs/architecture/** - Decyzje architektoniczne (ADRs)
5. **docs/tutorials/** - Howto guides
6. **docs/api-reference/** - API docs

### Przykład Dokumentacji

```python
def apply_homeostasis(self, arousal: float, pleasure: float, decay_rate: float = 0.95) -> Tuple[float, float]:
    """Apply homeostasis to return PAD vector to baseline.
    
    Homeostasis ensures the agent gradually returns to a calm state after
    emotional perturbations. This prevents emotional drift and burnout.
    
    Formula:
        - Arousal_new = Arousal_old × decay_rate
        - Pleasure_new = (Pleasure_old + baseline_pleasure) / 2
    
    Args:
        arousal: Current arousal level [0, 1]
        pleasure: Current pleasure level [-1, 1]
        decay_rate: Exponential decay factor [0.9, 0.99]
        
    Returns:
        Tuple of (new_arousal, new_pleasure)
        
    Example:
        >>> apply_homeostasis(arousal=0.5, pleasure=0.3)
        (0.475, 0.4)  # Both moved toward baseline
        
    Note:
        Called every 1 second in agent loop to maintain emotional health.
        Prevents accumulation of stress that could lead to paranoid mode.
    """
    new_arousal = arousal * decay_rate
    new_pleasure = (pleasure + self.baseline_pleasure) / 2
    return new_arousal, new_pleasure
```

---

## Getting Help

### Pytania?

- **Discord**: [Community Server](https://discord.gg/adrion369)
- **GitHub Issues**: [Create an issue](https://github.com/yourusername/AI-Agent-OS/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/AI-Agent-OS/discussions)
- **Email**: contact@adrion369.ai

### Problemy?

1. Sprawdź [FAQ](./docs/FAQ.md)
2. Szukaj w [issuach](https://github.com/yourusername/AI-Agent-OS/issues)
3. Stwórz nowy issue z szczegółami:
   - Co chcesz zrobić?
   - Co się stało?
   - Jakie błędy?
   - Jak zreprodukować?

---

## Acknowledgments

Dziękujemy wszystkim kontrybutorem którzy pracują nad ADRION 369! 

Szczególnie dziękujemy inspiracji z:
- Sacred geometry (3-6-9)
- Philosophy (Plato, Aristotle)
- Modern AI (Claude, GPT-4)
- Distributed systems
- Psychology & emotion

---

## License

Wszystkie contributions są akceptowane na warunkach [MIT License](../LICENSE).

---

**Last updated:** January 2026  
**Maintainers:** ADRION Core Team

Dziękujemy za bycie częścią naszej społeczności! 🚀
