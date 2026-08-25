🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

# 🎯 Soc Ops

A social bingo game for in-person mixers — built as a hands-on lab for learning **GitHub Copilot Agents** with **Java + Spring Boot + vanilla JavaScript**.

[![Java 21](https://img.shields.io/badge/Java-21-orange)](https://adoptium.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.2-6DB33F)](https://spring.io/projects/spring-boot)
[![Maven](https://img.shields.io/badge/Maven-Wrapper-C71A36)](https://maven.apache.org/)

- 📚 **Lab Guide:** [workshop/GUIDE.md](workshop/GUIDE.md)
- 🎮 **Live Demo:** https://copilot-dev-days.github.io/agent-lab-java/

---

## Why this project?

Soc Ops is both:

- A fun bingo game (5×5 board, 24 prompts + free center, 5-in-a-row wins)
- A practical lab to practice prompt design, multi-agent workflows, and TDD with Copilot

---

## 🚀 Quick Start

### Prerequisites

- [Java 21 JDK](https://adoptium.net/) or higher
- [Apache Maven 3.9+](https://maven.apache.org/) (or use the included Maven Wrapper)

### Run locally

```bash
cd socops
./mvnw spring-boot:run
```

Open: http://localhost:8080

### Build and test

```bash
cd socops
# Workshop validation checklist
./mvnw clean
./mvnw package -DskipTests
./mvnw test
```

---

## 🧭 Learn by doing

Follow the lab path:

| Part | Title |
|------|-------|
| [**00**](workshop/00-overview.md) | Overview & Checklist |
| [**01**](workshop/01-setup.md) | Setup & Context Engineering |
| [**02**](workshop/02-design.md) | Design-First Frontend |
| [**03**](workshop/03-quiz-master.md) | Custom Quiz Master |
| [**04**](workshop/04-multi-agent.md) | Multi-Agent Development |

> 📝 Offline reading: all guides are available in [`workshop/`](workshop/).

---

## 🏗️ Project highlights

- **Backend:** Spring Boot REST API (`/api/bingo/fresh-board`)
- **Frontend:** Single-page UI in `game.html` with local state persistence
- **Core logic:** Pure static board assembler and victory detection (easy to test)
- **Testing:** JUnit 5, deterministic tests without mocks

---

## 📦 Deployment

Pushes to `main` automatically deploy GitHub Pages content.

---

## 🤝 Contributing

If you want to contribute, start with:

- [CONTRIBUTING.md](CONTRIBUTING.md)
- [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)
- [SECURITY.md](SECURITY.md)
