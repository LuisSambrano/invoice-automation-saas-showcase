# Invoice Automation SaaS

[🇺🇸 English](README.md) | [🇵🇹 Português](README.pt.md)

<p align="center">
  <img src="https://img.shields.io/badge/Tauri_v2-FFC131?style=for-the-badge&logo=tauri&logoColor=black" alt="Tauri" />
  <img src="https://img.shields.io/badge/Rust-Backend-000000?style=for-the-badge&logo=rust" alt="Rust" />
  <img src="https://img.shields.io/badge/React_19-Frontend-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React 19" />
  <img src="https://img.shields.io/badge/SQLite-DB-003B57?style=for-the-badge&logo=sqlite" alt="SQLite" />
</p>

## 🏛️ Resumen del Proyecto

Este repositorio contiene el código fuente de una aplicación de escritorio _offline-first_ diseñada para la generación de facturas y la gestión financiera. Aprovechando el framework **Tauri v2**, el sistema vincula un backend de alto rendimiento en **Rust** con una interfaz frontend en **React 19**. La persistencia de datos es manejada internamente a través de una base de datos **SQLite** embebida, garantizando el aislamiento de la información y el desacoplamiento de cualquier infraestructura en la nube.

---

## ⚙️ Características Técnicas Principales

### 1. Arquitectura de Base de Datos Embebida

Implementación de un modelo de almacenamiento local utilizando SQLite a través de `sqlx`. Todos los datos transaccionales (clientes, facturas, productos) son encriptados en reposo y residen estrictamente dentro de los directorios AppData protegidos de la máquina host.

### 2. Interoperabilidad de Sistemas de Alto Rendimiento

El puente de Tauri facilita velocidades de ejecución casi nativas. Tareas intensivas en recursos, tales como la generación de archivos PDF y operaciones I/O del sistema de archivos, son delegadas al backend multi-hilo en Rust, previniendo el bloqueo en el hilo de renderizado del DOM de React.

### 3. Seguridad y Control de Memoria

El estricto modelo de propiedad (_ownership_) de Rust erradica vulnerabilidades comunes, como el desbordamiento de búfer y las referencias a punteros nulos. La aplicación no requiere conexión a la red externa, minimizando drásticamente la superficie de ataque.

---

## 🏗️ Visión General de la Arquitectura

```text
invoice-automation-saas/
├── src/                    # Código Cliente React 19
│   ├── components/        # Componentes UI aislados
│   ├── services/          # Lógica de negocio lado-cliente
│   └── types/             # Definiciones TypeScript
├── src-tauri/             # Backend en Rust
│   ├── src/
│   │   ├── main.rs       # Bootstrap de la aplicación primaria
│   │   ├── commands.rs   # Controladores de IPC (Inter-Process Comms) en Tauri
│   │   └── database.rs   # Ejecución y conexión en pool para SQLite
│   └── Cargo.toml        # Perfil de dependencias Rust
└── package.json          # Dependencias generales de Node
```

**Stack Tecnológico Enterprise:**

- **Motor Central:** Rust
- **Framework de Escritorio:** Tauri v2
- **Capa Frontend:** React 19, Tailwind CSS
- **Base de Datos Local:** SQLite
- **Análisis Estático:** TypeScript (Modo Estricto)

---

## ⚡ Instalación y Desarrollo

### Prerrequisitos

- **Rust Toolchain**: Instalación a través de `rustup`
- **Node.js**: `v20+`
- **Dependencias de Plataforma**: Xcode CLI (macOS), Visual Studio Build Tools (Windows), o paquetes como `build-essential` & `libwebkit2gtk` (Linux).

### Instrucciones de Preparación

1. **Clonar el repositorio:**

   ```bash
   git clone https://github.com/LuisSambrano/invoice-automation-saas.git
   cd invoice-automation-saas
   ```

2. **Instalar las dependencias del frontend:**

   ```bash
   npm install
   ```

3. **Ejecutar el entorno de desarrollo local:**
   ```bash
   npm run tauri dev
   ```

### Build en Producción

Crea binarios compilados y firmados de acuerdo al sistema operativo anfitrión:

```bash
# macOS (Compilación binaria nativa/Universal)
npm run tauri build -- --target universal-apple-darwin

# Windows (MSI / Archivo ejecutable)
npm run tauri build
```

---

## 🎨 Estándares de Código

Este repositorio hace cumplir rigurosos estándares de ingeniería de software:

1. `npm run lint` debe resultar en cero errores dentro del directorio frontend.
2. `cargo fmt` y `cargo clippy` deben aprobarse de extremo a extremo cubriendo todo el sub-proyecto Rust.
3. No se admiten tipos dinámicos superpuestos como `any` en TS; haz uso de variables `unknown` analizadas por Type Guards locales.
4. Es obligatorio establecer historiales atómicos vía _Conventional Commits_.

---

## 📄 Licencia y Contribución

Este proyecto está liberado para inspección estructural bajo los términos de la [Business Source License 1.1](./LICENSE). Las iniciativas de despliegue comercial deben atenerse a licencias especializadas apartes. Visita el documento `.agent/rules/PROTOCOL_ZERO.md` para visualizar los lineamientos arquitectónicos.
