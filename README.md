<div align="center">

<!-- HEADER -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=2,6,11&height=200&section=header&text=Invoice%20Automation&fontSize=50&fontColor=fff&animation=twinkling&fontAlignY=35&desc=SaaS%20Platform%20%7C%20Financial%20Management%20%7C%20Open%20Source&descSize=18&descAlignY=55"/>

<!-- BADGES -->
<p>
  <img src="https://img.shields.io/badge/Type-Desktop_SaaS-blueviolet?style=for-the-badge" alt="Type: Desktop SaaS"/>
  <img src="https://img.shields.io/badge/Tauri_v2-FFC131?style=for-the-badge&logo=tauri&logoColor=black" alt="Tauri" />
  <img src="https://img.shields.io/badge/Rust-Backend-000000?style=for-the-badge&logo=rust" alt="Rust" />
  <img src="https://img.shields.io/badge/React_19-Frontend-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React 19" />
  <img src="https://img.shields.io/badge/SQLite-DB-003B57?style=for-the-badge&logo=sqlite" alt="SQLite" />
</p>

<!-- LANGUAGE SWITCHER -->
<p>
  <a href="./README.md"><img src="https://img.shields.io/badge/🇺🇸_English-Selected-blue?style=flat-square" alt="English"/></a>
  <a href="./README.es.md"><img src="https://img.shields.io/badge/🇪🇸_Español-Available-lightgrey?style=flat-square" alt="Español"/></a>
  <a href="./README.pt.md"><img src="https://img.shields.io/badge/🇧🇷_Português-Available-lightgrey?style=flat-square" alt="Português"/></a>
</p>

</div>

---

**An offline-first desktop application engineered for high-performance invoice generation and financial management using Tauri v2, Rust, and React 19.**

---

## 🏛️ Project Abstract

This repository contains the source code for an offline-first desktop application engineered for invoice generation and financial management. By leveraging the **Tauri v2** framework, the system binds a high-performance **Rust** backend with a **React 19** frontend interface. Data persistence is handled internally via an embedded **SQLite** database, guaranteeing data isolation and decoupling from external cloud infrastructure.

---

## ⚙️ Core Technical Features

### 1. Embedded Database Architecture

Implementation of a local-first storage model using SQLite via `sqlx`. All transactional data (clients, invoices, items) is encrypted at rest and resides strictly within the host machine's protected AppData directories.

### 2. High-Performance Systems Interop

The Tauri bridge facilitates near-native execution speeds. Resource-intensive tasks, such as PDF generation and file system I/O operations, are delegated to the multi-threaded Rust backend, preventing blocking on the React DOM rendering thread.

### 3. Memory Safety & Security

Rust's strict ownership model eradicates customary vulnerabilities such as buffer overflows and null pointer dereferences. The application requires zero ambient network access, significantly minimizing the attack surface.

---

## 🏗️ Technical Architecture Overview

```text
invoice-automation-saas/
├── src/                    # React 19 Client Code
│   ├── components/        # Isolated UI components
│   ├── services/          # Client-side business logic
│   └── types/             # TypeScript definitions
├── src-tauri/             # Rust Backend
│   ├── src/
│   │   ├── main.rs       # Application bootstrap
│   │   ├── commands.rs   # Tauri Inter-Process Communication (IPC) handlers
│   │   └── database.rs   # SQLite connection pool and query execution
│   └── Cargo.toml        # Rust dependencies profile
└── package.json          # Node dependencies
```

**Enterprise Tech Stack:**

- **Core Engine:** Rust
- **Desktop Framework:** Tauri v2
- **Frontend Layer:** React 19, Tailwind CSS
- **Database:** SQLite
- **Static Analysis:** TypeScript (Strict Mode)

---

## ⚡ Installation & Development

### Prerequisites

- **Rust Toolchain**: Install via `rustup`
- **Node.js**: `v20+`
- **Platform Dependencies**: Xcode CLI (macOS), Visual Studio Build Tools (Windows), or `build-essential` & `libwebkit2gtk` (Linux).

### Setup Instructions

1. **Clone the repository:**

   ```bash
   git clone https://github.com/LuisSambrano/invoice-automation-saas.git
   cd invoice-automation-saas
   ```

2. **Install frontend dependencies:**

   ```bash
   npm install
   ```

3. **Run the local development environment:**
   ```bash
   npm run tauri dev
   ```

### Production Build

Create signed binaries according to your host operating system:

```bash
# macOS (Universal binary compiling)
npm run tauri build -- --target universal-apple-darwin

# Windows (MSI / EXE)
npm run tauri build
```

---

## 🎨 Code Standards

This repository enforces strict engineering standards:

1. `npm run lint` must yield zero frontend errors.
2. `cargo fmt` and `cargo clippy` must pass securely across the entire Rust backend.
3. No `any` types allowed in TS; use strict typing or `unknown` with Type Guards.
4. Conventional Commits are required for version control.

---

## 📄 License & Contributing

This project is open for inspection under the [Business Source License 1.1](./LICENSE). Commercial deployment or distribution of compiled binaries requires specialized licensing. View `.agent/rules/PROTOCOL_ZERO.md` for our internal guidelines.

---

<div align="center">

_Architected by **Luis Sambrano**_

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=2,6,11&height=100&section=footer"/>

</div>
