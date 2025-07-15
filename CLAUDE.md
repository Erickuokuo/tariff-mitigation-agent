### 🔄 Project Awareness & Context

- **Always read `PLANNING.md`** before contributing to understand project goals, agent design, and naming conventions.
- **Check `TASK.md`** before starting new work. If the task isn’t listed, add it with a short summary and today’s date.
- **Follow naming conventions and file structures** described in `PLANNING.md`.
- **Use `venv_linux` or your virtual environment** when running or testing Python scripts.

---

### 🧱 Code Structure & Modularity

- **Avoid files larger than 500 lines.** Break large logic into clearly separated modules:
  - `router_agent.py` – Determines user intent and dispatches tasks
  - `context_agent.py` – Tracks conversation and widget state
  - `classification_agent.py` – Handles HS code mapping
  - `sourcing_agent.py` – Generates strategy and alternatives
  - `tools/` – All callable tool functions
  - `prompts/` – System instructions and agent personalities
- **Use relative imports** where possible to maintain modularity.
- **Use `python_dotenv` and `load_env()`** for loading API keys or configs.

---

### 🤖 Crew AI-Specific Conventions

- **Use `crewai.Agent`** for all agents. Define:
  - `name`, `role`, `goal`, and `backstory` clearly
- **Use `Task` and `Crew` objects** to orchestrate multi-step workflows
- **Agents should only access tools they are explicitly assigned**
- **Tools must be callable functions with clear I/O**
- **Use decorators or schemas if chaining tool outputs to agents**

---

### 🧪 Testing & Reliability

- **Use Pytest** for unit testing agents, tools, and shared logic.
- **Structure tests under `/tests`**, mirroring main app modules.
  - Include:
    - 1 test for normal behavior
    - 1 for edge case
    - 1 for failure/error path
- **Mock external API responses** and Crew agent output for reproducible test behavior.

---

### ✅ Task Completion

- **Mark completed items in `TASK.md`** immediately.
- Add subtasks or bugs discovered during dev under “Discovered During Work”.

---

### 📎 Style & Conventions

- **Use Python 3.10+**
- **Follow PEP8**, format with `black`, and lint with `ruff` or `flake8`.
- **Use type hints and docstrings** on all functions.
- **Docstring format** (Google-style):
  ```python
  def suggest_strategy(component: str) -> str:
      """
      Suggests a sourcing strategy for a given component.

      Args:
          component (str): Component name.

      Returns:
          str: Recommended sourcing strategy.
      """
