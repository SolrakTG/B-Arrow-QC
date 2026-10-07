# 🔬 B-Arrow QC — Clinical Quality Control & Six Sigma Suite

[![Version](https://img.shields.io/badge/Versión-v1.0.0-0ea5e9?style=for-the-badge&logo=github)](https://github.com/SolrakTG/B-Arrow-QC/releases/latest)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Norma](https://img.shields.io/badge/Estándar-ISO%2015189%3A2022-2ECC71?style=for-the-badge)](https://www.iso.org/standard/76677.html)
[![Plataforma](https://img.shields.io/badge/Plataforma-Windows%2010%20%7C%2011-0078D6?style=for-the-badge&logo=windows)](https://microsoft.com)

**B-Arrow QC** es una plataforma clínica de escritorio desarrollada para el aseguramiento de la calidad analítica, gestión metrológica y evaluación estadística en laboratorios clínicos y servicios de medicina transfusional. Integra procesamiento de reportes de analizadores, reglas multirregla de Westgard, métricas Six Sigma, cartas de control dinámicas y auditoría forense para acreditación bajo la norma ISO 15189:2022.

---

## 📌 Tabla de Contenidos
- [Características Principales](#-características-principales)
- [Módulos del Sistema](#-módulos-del-sistema)
- [Arquitectura y Persistencia](#-arquitectura-y-persistencia)
- [Descarga e Instalación](#-descarga-e-instalación)
- [Credenciales de Acceso](#-credenciales-de-acceso-primer-inicio)
- [Sistema de Actualizaciones Remotas (OTA)](#-sistema-de-actualizaciones-remotas-ota)
- [Autoría y Contacto](#-autoría-y-contacto)

---

## 🚀 Características Principales

* **Ingesta Multi-Formato & Conectividad LIS:** Procesamiento directo y por arrastre (*drag & drop*) de reportes de control generados en analizadores (archivos PDF, CSV, Excel y TXT). Soporta carga de rutina diaria y procesamiento de históricos consolidados (*multi-partes*).
* **Evaluación Multirregla de Westgard:** Análisis automatizado de violaciones operativas ($1_{3\text{s}}$, $2_{2\text{s}}$, $R_{4\text{s}}$, $4_{1\text{s}}$, $10_{\overline{x}}$) alineado a las directrices CLSI C24 y EP29.
* **Métrica Six Sigma Analítica:** Cálculo dinámico de CV%, Sesgo (Bias) y métrica Sigma frente al Error Total Máximo ($TE_a$) establecido por CLIA, SEQC o especificaciones de variabilidad biológica.
* **Discriminación Inteligente de Matrices:** Detección contextual de magnitudes bioquímicas en distintas matrices analíticas (ej. separación automatizada de Creatinuria en orina frente a Creatinemia en suero).
* **Visualización Gráfica Avanzada:**
  * Curvas de Levey-Jennings interactivas con control multinivel.
  * Diagramas Youden Twin-Plot para la diferenciación cuantitativa de error analítico sistemático versus aleatorio.
* **Optimización Operativa:** Modo de exportación e impresión en blanco y negro de alto contraste, reduciendo costos de tinta y tóner en entornos asistenciales.
* **Acreditación ISO 15189:** Módulo de bitácora para gestión de No Conformidades y registro forense (*Audit Log*) para trazabilidad de cada corrida analítica.

---

## 🧩 Módulos del Sistema

| Módulo | Descripción Funcional |
| :--- | :--- |
| **Dashboard Analítico** | Visión general del día: corridas procesadas, salud analítica global, equipos activos y estado de la bóveda SQL. |
| **Monitor en Vivo** | Vista inmediata de las últimas corridas ingresadas con estado de conformidad analítica. |
| **Gráficas QC** | Cartas de control Levey-Jennings por analizador, analito y nivel con cálculo de límites $1\text{s}$, $2\text{s}$ y $3\text{s}$. |
| **Youden Twin-Plot** | Evaluación bivariada simultánea de dos niveles de control para identificar desvíos interanálisis. |
| **Incertidumbre Analítica** | Estimación metrológica estandarizada de la incertidumbre expandida ($U$) según requisitos ISO 15189. |
| **Bitácora de No Conformidades** | Registro de desvíos, análisis de causa raíz y seguimiento de acciones correctivas. |
| **Registro Forense (Audit Log)** | Trazabilidad completa e inmutable de eventos, modificaciones y firmas operativas. |
| **Informe Ejecutivo** | Generación de resúmenes consolidados en PDF para dirección técnica y jefatura de laboratorio. |

---

## 🏛️ Arquitectura y Persistencia

El software implementa un modelo de aislamiento de datos diseñado para operar en redes hospitalarias sin riesgo de pérdida de información:

* **Bóveda SQL Local:** Los datos clínicos se almacenan en una base SQLite estructurada en `%LOCALAPPDATA%\BArrowQC\LIS_Database.db`.
* **Protección ante Actualizaciones:** Los binarios de la aplicación permanecen separados de la base de datos, asegurando que cualquier actualización de versión mantenga intacto el historial analítico del laboratorio.
* **Migración Automática:** Detecta instalaciones previas de la suite y transfiere automáticamente configuraciones y registros existentes sin intervención del usuario.

---

## 💻 Descarga e Instalación

La aplicación se distribuye como paquete ejecutable portable y no requiere privilegios de administrador para operar en las estaciones de trabajo clínicas:

1. Dirígete a la sección de [Releases de B-Arrow QC](https://github.com/SolrakTG/B-Arrow-QC/releases/latest).
2. Descarga el paquete `B-Arrow_QC_Update.zip` de la última versión oficial.
3. Descomprime el contenido en una carpeta local (por ejemplo en el Escritorio o disco `C:\`).
4. Ejecuta `B-Arrow_QC.exe`.

> **Nota para Windows Defender / SmartScreen:**  
> Al tratarse de un ejecutable independiente de ámbito clínico, en el primer inicio Windows puede desplegar la ventana azul de advertencia de SmartScreen. Haz clic en **«Más información»** y posteriormente en el botón **«Ejecutar de todas formas»**.

---

## 🔐 Credenciales de Acceso (Primer Inicio)

Al iniciar el sistema por primera vez, puedes ingresar con cualquiera de los perfiles preconfigurados:

| Rol | Usuario | Contraseña | Permisos |
| :--- | :--- | :--- | :--- |
| **SuperAdmin / Auditor** | `admin` | `admin` | Acceso irrestricto, auditoría forense, gestión de analizadores y firmas. |
| **Técnico Operador** | `user` | `user` | Procesamiento diario, gráficos de control e ingreso manual de resultados. |

---

## 🔄 Sistema de Actualizaciones Remotas (OTA)

B-Arrow QC incorpora un mecanismo cliente-servidor para el despliegue desatendido de parches:

1. Al arrancar, el programa consulta de forma asíncrona la especificación de versión oficial en GitHub.
2. Si se detecta un parche disponible, despliega la ventana modal con las novedades y notas de versión.
3. Al autorizar la actualización, el proceso autónomo `updater.exe` descarga el paquete, cierra el software principal, reemplaza los binarios y reabre la plataforma automáticamente sin perder datos ni configuraciones.

---

## 👨‍🔬 Autoría y Contacto

**Desarrollado por:**
* **TM Carlos Torres Garrido**  
  *Tecnólogo Médico • Laboratorio Clínico, Hematología y Banco de Sangre*  
  *Desarrollador de Middleware LIS Clínico & Bioestadística Avanzada*

* 📧 **Correo Electrónico:** [tm.carlostg@gmail.com](mailto:tm.carlostg@gmail.com)
* 💼 **Perfil Profesional:** [LinkedIn](https://www.linkedin.com/in/tmcarlostg)
* 🏛️ **Repositorio Oficial:** [SolrakTG/B-Arrow-QC](https://github.com/SolrakTG/B-Arrow-QC)

---

*Desarrollado bajo principios de aseguramiento metrológico para laboratorios clínicos (ISO 15189:2022 / CLSI C24).*
