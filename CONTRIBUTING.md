# Contributing to ADRION

Thank you for your interest in contributing to the ADRION project! 🙏

---

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Contributor Process](#contributor-process)
- [Coding Guidelines](#coding-guidelines)
- [Commit Structure](#commit-structure)
- [PR Process](#pr-process)
- [Tests](#tests)
- [Documentation](#documentation)
- [Getting Help](#getting-help)

---

## Code of Conduct

### Our Principles

The ADRION 369 project is built on **9 Ethical Laws**. We expect all contributors to respect these principles:

#### 🤝 **Law 1: Unity**
- Act for the common good, not for personal gain
- Support other team members
- Share knowledge and experience
- Resolve conflicts constructively

#### 🧠 **Law 2: Truth**
- Be honest in communication and code
- Admit mistakes and learn from them
- Verify information before publishing it
- Do not manipulate or lie

#### ⏰ **Law 3: Rhythm**
- Work in healthy cycles (not workaholism)
- Respect other people's time
- Respond within a reasonable time (24-48h)
- Taking breaks is OK and encouraged

#### ➡️ **Law 4: Causality**
- Document WHY, not just WHAT
- Explain your logic in PRs/commits
- Be accountable for your code
- Track the consequences of changes

#### 👀 **Law 5: Transparency**
- Communicate clearly and openly
- Be available for questions and review
- Don't hide problems - talk about them early
- Share decisions and their justifications

#### 🛡️ **Law 6: Nonmaleficence**
- Don't break existing code without reason
- Test before push
- Communicate breaking changes
- Minimize risk to production

#### 🗳️ **Law 7: Autonomy**
- Respect other people's decisions
- Don't force your ideas
- Accept constructive criticism
- Let others choose their own path

#### ⚖️ **Law 8: Justice**
- Pay attention to underrepresented people
- Do not discriminate
- Give everyone an equal chance
- Be fair in assessing contributions

#### 🌱 **Law 9: Sustainability**
- Write code that will be understandable in 2 years
- Invest in long-term (not hacks)
- Take care of technical debt
- Think about the future of the project

### Consequences of Violation

Violation of this Code of Conduct may lead to:
- Notice (first time)
- Warnings (repetition)
- Temporary suspension (serious violations)
- Permanent ban (repeated violations)

---

## Getting Started

### 1. Set Up Environment

```bash
# Clone repository
git clone https://github.com/Gruszkoland/AI-Agent-OS.git
cd AI-Agent-OS

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
# or
venv\Scripts\activate  # Windows

# Install dependencies
pip install -r requirements.txt
pip install -r requirements-dev.txt

# Install pre-commit hooks
pre-commit install
```

### 2. Create Branch

```bash
git checkout -b feature/your-feature-name
```

### 3. Start Working

```bash
# Make sure tests pass
python -m pytest tests/

# Check linting
flake8 adrion/ tests/
black --check adrion/ tests/
mypy adrion/

# Format code
black adrion/ tests/
```

---

## Contributor Process

### Steps:

1. **Fork** the repository
2. **Clone** your fork
3. **Create** feature branch (`git checkout -b feature/amazing-feature`)
4. **Make** changes
5. **Test** your code
6. **Commit** changes (`git commit -m 'Add amazing feature'`)
7. **Push** to branch (`git push origin feature/amazing-feature`)
8. **Open** Pull Request
9. **Respond** to review comments
10. **Merge** (when approved)

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

## Coding Guidelines

### Python Style

Follow **PEP 8** and **Google Python Style Guide**:

```python
# ✓ GOOD CODE

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


# ✗ BAD CODE

def analyze(r, t=5000):
    """Analyze."""
    m = analyze_mat(r, t)
    i = analyze_int(r, t)
    e = analyze_ess(r, t)
    s = (m + i + e) / 3
    return s
```

### Type Hints

Always use type hints:

```python
# ✓ GOOD CODE
def process_task(task_id: str, agent: Agent) -> Task:
    """Process a task."""
    pass

# ✗ BAD CODE
def process_task(task_id, agent):
    """Process a task."""
    pass
```

### Documentation

Every function must have a **docstring**:

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

### Naming

```python
# ✓ GOOD CODE - clear and descriptive
class TrinityScoringEngine:
    def calculate_material_score(self, analysis: MaterialAnalysis) -> float:
        pass

# ✗ BAD CODE - unclear
class TSE:
    def calc_m_s(self, a):
        pass
```

### Code Structure

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

## Commit Structure

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code formatting (no logic)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding/modifying tests
- `chore`: Tooling changes, dependencies

### Examples

```bash
# ✓ GOOD COMMIT
git commit -m "feat(trinity): add material perspective analyzer

- Implement physical_analyzer for CPU/RAM metrics
- Implement energy_analyzer for power consumption
- Implement information_analyzer for data quality
- Add integration tests

Fixes #123"

# ✗ BAD COMMIT
git commit -m "fix stuff"
git commit -m "WIP: random changes"
```

---

## PR Process

### Before Submitting

1. **Rebase** on latest `main`
2. **Tests** pass locally
3. **Linting** passes
4. **Documentation** updated
5. **Changelog** updated

### PR Checklist

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
- [ ] Tests written and passing
- [ ] Code linted
- [ ] Documentation updated
- [ ] Not introducing breaking changes (unless intentional)
- [ ] Commit messages are clean
- [ ] CHANGELOG.md updated

## Related Issues
Fixes #123
Related to #456
```

### Code Review

When someone gives you review comments:

1. **Read carefully** - they're trying to help you
2. **Respond politely** - explain your approach
3. **Implement** - make changes quickly
4. **Re-request review** - when you're done
5. **Thank** - we're all working for the common good

---

## Tests

### Requirements

- Minimum 80% code coverage
- All tests must pass
- New features = new tests

### Structure

```
tests/
├── unit/                    # Testing functions/methods
│   ├── test_trinity.py
│   ├── test_hexagon.py
│   └── test_perspectives.py
├── integration/            # Testing communication
│   ├── test_system_flow.py
│   └── test_agent_coordination.py
└── e2e/                   # End-to-end scenarios
    ├── test_complete_request.py
    └── test_emotional_regulation.py
```

### Writing Tests

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

### Running Tests

```bash
# Run all tests
python -m pytest

# Run tests with coverage
python -m pytest --cov=adrion tests/

# Run specific test
python -m pytest tests/unit/test_trinity.py::TestTrinity::test_trinity_score_calculation

# Run with verbose output
python -m pytest -v

# Run only integration tests
python -m pytest tests/integration/
```

---

## Documentation

### Where to Document

1. **Code comments** - WHY, not WHAT (code shows WHAT)
2. **Docstrings** - Every function/class
3. **README** - General introduction
4. **docs/architecture/** - Architectural decisions (ADRs)
5. **docs/tutorials/** - Howto guides
6. **docs/api-reference/** - API docs

### Documentation Example

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

### Questions?

- **Discord**: [Community Server](https://discord.gg/adrion369)
- **GitHub Issues**: [Create an issue](https://github.com/Gruszkoland/AI-Agent-OS/issues)
- **Discussions**: [GitHub Discussions](https://github.com/Gruszkoland/AI-Agent-OS/discussions)
- **Email**: contact@adrion369.ai

### Problems?

1. Check the [FAQ](./docs/FAQ.md)
2. Search in [issues](https://github.com/Gruszkoland/AI-Agent-OS/issues)
3. Create a new issue with details:
   - What do you want to do?
   - What happened?
   - What errors?
   - How to reproduce?

---

## Acknowledgments

Thank you to all contributors working on ADRION 369!

Special thanks for inspiration from:
- Sacred geometry (3-6-9)
- Philosophy (Plato, Aristotle)
- Modern AI (Claude, GPT-4)
- Distributed systems
- Psychology & emotion

---

## License

All contributions are accepted under the terms of the [MIT License](../LICENSE).

---

**Last updated:** January 2026  
**Maintainers:** ADRION Core Team

Thank you for being part of our community! 🚀
