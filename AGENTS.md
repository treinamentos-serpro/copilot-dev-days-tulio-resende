---
name: Soc Ops — Social Bingo Game
description: Lab environment for learning VS Code GitHub Copilot agents and multi-agent development with Java Spring Boot and vanilla JavaScript.
---

# Soc Ops — Copilot Agents Instructions

[📚 **Lab Guide**](workshop/GUIDE.md) | [🎮 **Live Demo**](https://copilot-dev-days.github.io/agent-lab-java/) | [← **README**](README.md)

---

## ✅ Development Checklist (Before Committing)

```bash
cd socops

# 1. LINT & FORMAT
./mvnw clean  # Fresh build

# 2. BUILD
./mvnw package -DskipTests

# 3. TEST
./mvnw test
```

**All three must pass before creating a PR.**

---

## 🎯 Project at a Glance

**Soc Ops** — Social bingo game for in-person mixers (5×5 grid, 24 prompts, 5-in-a-row wins).

- **Stack**: Spring Boot 3.4.2 + Java 21 + Vanilla JS + Custom CSS
- **Key Files**: `BoardAssembler.java` (logic), `BingoRestController.java` (API), `game.html` (UI)
- **Testing**: JUnit 5, pure static methods (no mocks)
- **Deploy**: GitHub Actions auto-deploys on push to `main`

### Commands (run from `socops/`)

```bash
./mvnw spring-boot:run      # Dev server (port 8080)
./mvnw test                 # Run tests
./mvnw clean package        # Build JAR
```

---

## 🏗️ Architecture Patterns

| Pattern | File | Key Idea |
|---------|------|----------|
| **Static Service** | [`BoardAssembler.java`](socops/src/main/java/com/socops/service/BoardAssembler.java) | All static, zero Spring deps, testable in isolation |
| **Records (DTOs)** | [`BingoCell.java`](socops/src/main/java/com/socops/model/BingoCell.java) | Java 21 records = auto getters/equals/toString |
| **REST + Client State** | [`BingoRestController.java`](socops/src/main/java/com/socops/web/BingoRestController.java) | Server provides `/api/bingo/fresh-board`, client manages state |
| **Single-Page UI** | [`game.html`](socops/src/main/resources/templates/game.html) | 3 phases (LOBBY, ACTIVE, VICTORY) + localStorage persistence |
| **Mirrored Logic** | `BoardAssembler.java` ↔ `game.html` | Both implement identical victory detection (5-in-a-row scan) |

---

## 📂 Project Structure

```
socops/
├── src/main/java/com/socops/
│   ├── web/                  → BingoRestController (REST)
│   ├── service/              → BoardAssembler (pure logic)
│   ├── model/                → BingoCell, PlayPhase, WinningStreak (records)
│   └── data/                 → IcebreakerPrompts (24 strings, exactly)
├── src/main/resources/
│   ├── templates/game.html   → Single-page UI + JS + Thymeleaf
│   └── static/css/app.css    → Custom utility classes
└── src/test/java/com/socops/service/
    └── BoardAssemblerTests.java  → JUnit 5 tests

workshop/                     → 5-part lab guide (3 languages)
docs/                         → GitHub Pages (auto-deployed)
.github/instructions/         → CSS utilities, frontend design guidelines
```

---

## 📋 Conventions & Key Facts

| Aspect | Rule | Reference |
|--------|------|-----------|
| **Grid** | 5×5 = 25 cells; center = free cell; exactly 24 prompts | `BoardAssembler.java` |
| **Victory** | 5 in a row (horizontal, vertical, or diagonal) | `detectWinningStreak()` |
| **Java Naming** | PascalCase classes, camelCase methods | Standard |
| **Frontend** | Vanilla ES5 (no const/let), utility CSS, localStorage for state | `game.html`, `app.css` |
| **Testing** | `*Tests.java`, `@DisplayName`, Arrange-Act-Assert, no mocks | `BoardAssemblerTests.java` |
| **CSS** | Compose utilities, no inline styles, avoid Tailwind CDN | See `.github/instructions/` |

---

## 🔧 Common Tasks

| Task | Steps |
|------|-------|
| Add prompt | Edit `IcebreakerPrompts.java`, keep exactly 24 total |
| Change color | Update `.bg-accent` hex in `app.css` |
| Add test | Create `@Test @DisplayName("...")` in `BoardAssemblerTests.java` |
| New game phase | Add to `PlayPhase` enum + JS `showPhase()` branch |
| Debug logic | Reproduce in test first (pure, deterministic) |
| Deploy | Push to `main` → GitHub Actions auto-triggers |

---

## 🚀 Agent Workflows

**Recommended Agents:**
1. **Pixel Jam** — Design UI (read [`.github/instructions/frontend-design.instructions.md`](.github/instructions/frontend-design.instructions.md) first)
2. **Quiz Master** — Generate bingo prompts (output: 24 Java strings)
3. **TDD Supervisor** — Full TDD cycle (Red → Green → Refactor)
4. **Explore** — Quick codebase Q&A
5. **UI Review** — Frontend polish

See [`workshop/04-multi-agent.md`](workshop/04-multi-agent.md) for multi-agent workflow examples.

---

## 📚 Quick Links

- **Lab Guide:** [`workshop/GUIDE.md`](workshop/GUIDE.md)
- **CSS Utilities:** [`.github/instructions/css-utilities.instructions.md`](.github/instructions/css-utilities.instructions.md)
- **Frontend Design:** [`.github/instructions/frontend-design.instructions.md`](.github/instructions/frontend-design.instructions.md)
- **Full README:** [README.md](README.md)

---

**Ready to build! 🚀**
