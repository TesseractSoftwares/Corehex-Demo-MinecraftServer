# Core-Hex: Sistema de Despliegue de Servidores Minecraft con Docker

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Minecraft](https://img.shields.io/badge/Minecraft-5C824A?style=for-the-badge&logo=minecraft&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)

Sistema modular para el despliegue automático de una red de servidores de Minecraft, utilizando Docker para una fácil configuración y escalabilidad.

---

## 📜 Descripción General

Este proyecto proporciona una infraestructura basada en contenedores para levantar rápidamente una red de servidores de Minecraft interconectados. El objetivo es facilitar un entorno de desarrollo y producción que sea modular, permitiendo que diferentes tipos de servidores (Lobby, Minijuegos, etc.) coexistan y se comuniquen de manera eficiente.

### ✨ Características Principales

* **Red con Proxy:** Utiliza **Velocity** como proxy de entrada para redirigir a los jugadores y gestionar la red.
* [cite_start]**Servidores de Juego Modernos:** Los servidores de juego corren sobre **PaperMC 1.20.1**, una versión de alto rendimiento de Spigot. [cite: 2]
* **Modularidad:** La estructura está diseñada para que cada servidor cargue sus propios mundos y plugins, permitiendo configuraciones específicas por modalidad.
* [cite_start]**Listo para Desplegar:** Orquestado con **Docker Compose** para un inicio rápido y sencillo con un solo comando. [cite: 1, 2]
* [cite_start]**Escalabilidad:** Diseñado con un enfoque de escalabilidad horizontal, facilitando la adición de nuevas instancias de servidores de juego. [cite: 1]

---

## 🔌 Arquitectura de Plugins

El sistema está configurado para cargar plugins específicos según el rol de cada servidor, promoviendo la modularidad.

### Proxy (Velocity)

[cite_start]El servidor proxy carga los siguientes plugins para gestionar la red y la seguridad[cite: 6]:
* **LuckPerms:** Para la gestión centralizada de permisos.
* **AdvancedPortals:** Para el sistema de portales a través de la red.
* **EnhancedVelocity:** Funcionalidades adicionales para el proxy.
* **SayanVanish:** Sistema de "vanish" a nivel de proxy.
* **VelocityRcon:** Habilita el acceso RCON para administración remota.

### Servidores de Juego (Paper)

Los servidores backend utilizan una combinación de plugins comunes y específicos. [cite_start]La siguiente tabla detalla la distribución actual[cite: 6]:

| Plugin | Lobby (`lobby1`) | Minijuegos (`minigames`) | Construcción (`builds`) | Descripción |
| :--- | :---: | :---: | :---: | :--- |
| **NexusCraftPlugin** | ✅ | ✅ | ❌ | Plugin principal del proyecto (Core). |
| **LuckPerms** | ✅ | ✅ | ✅ | Gestiona los permisos de los jugadores. |
| **WorldEdit** | ✅ | ✅ | ✅ | Herramienta de edición de mundos. |
| **WorldGuard** | ✅ | ✅ | ✅ | Protege zonas y regiones del mundo. |
| **AdvancedPortals**| ✅ | ✅ | ✅ | Permite la creación de portales. |
| **AxiomPaper** | ❌ | ❌ | ✅ | Plugin de construcción avanzada para el servidor de `builds`. |
| **GriefPrevention** | ❌ | ✅ | ❌ | Sistema de protección de construcciones para el servidor de `minigames`. |
| **~~SayanVanish~~** | ⚠️ | ⚠️ | ⚠️ | [cite_start]**(Presenta errores)** Plugin de vanish para servidores Paper. [cite: 2, 4] |

*Leyenda: ✅ Instalado, ❌ No Instalado, ⚠️ Presenta Errores de Compatibilidad.*

---

## 🚀 Guía de Inicio Rápido (Getting Started)

Sigue estos pasos para levantar el sistema completo en tu propio entorno.

### Requisitos Previos

* [**Docker**](https://www.docker.com/products/docker-desktop/) y **Docker Compose** instalados.
* [**Git**](https://git-scm.com/downloads) instalado para clonar el repositorio.

### Instalación y Ejecución

1.  **Clona el repositorio:**
    ```bash
    git clone [https://github.com/TesseractSoftwares/Corehex-Demo-MinecraftServer.git](https://github.com/TesseractSoftwares/Corehex-Demo-MinecraftServer.git)
    ```

2.  **Navega al directorio del proyecto:**
    ```bash
    cd Corehex-Demo-MinecraftServer
    ```

3.  **Navega a la carpeta de configuración de Docker:**
    ```bash
    cd server_docker
    ```

4.  **Levanta la red de servidores:**
    *Este comando construirá las imágenes y levantará todos los contenedores definidos.*
    ```bash
    docker-compose up --build
    ```

5.  **¡Conéctate y Juega!**
    * [cite_start]Una vez que los servidores hayan iniciado, abre tu cliente de Minecraft en la versión **1.20.1**. [cite: 2]
    * Añade un nuevo servidor con la dirección: `localhost`

---

## 🤝 Contribuciones

Este es un proyecto de código abierto. Las contribuciones son bienvenidas. Para contribuir, por favor, sigue el siguiente flujo de trabajo:

1.  Haz un "Fork" del repositorio.
2.  Crea una nueva rama para tu funcionalidad (`git checkout -b feature/AmazingFeature`).
3.  Realiza tus cambios y haz "commit" de ellos (`git commit -m 'Add some AmazingFeature'`).
4.  Sube tus cambios a tu rama (`git push origin feature/AmazingFeature`).
5.  [cite_start]Abre un "Pull Request" para que podamos revisar e integrar tus cambios. [cite: 5]