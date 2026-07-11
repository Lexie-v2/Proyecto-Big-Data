# Diseño e Implementación de un Modelo de Forecasting para la Optimización de Ventas y Utilidades en una Plataforma de E-Commerce mediante Algoritmos de Regresión

## 📖 Descripción del Proyecto
Este proyecto de Big Data y Analítica de Datos tiene como objetivo diseñar e implementar un pipeline completo en la nube para capturar, procesar y proyectar las ventas y márgenes de utilidad de una plataforma de e-commerce. La arquitectura evoluciona desde un enfoque transaccional relacional tradicional hacia un entorno de procesamiento distribuido y analítica predictiva avanzada en la nube, garantizando el gobierno de datos y el cumplimiento de normativas internacionales de seguridad de la información.

## 🏗️ Arquitectura del Sistema
El ecosistema de datos está estructurado bajo una **Arquitectura de Capas (Layered Architecture)** soportada por un flujo de pipeline progresivo tipo ETL (Extract, Transform, Load):

1. **Capa de Ingesta:** Dataset transaccional heterogéneo original (3,500 registros estructurados en formato JSON / NoSQL).
2. **Capa de Almacenamiento Cloud:** Base de datos analítica relacional con diseño de Modelo de Estrella, normalizada en **MySQL** y alojada en la plataforma cloud de **Aiven**.
3. **Capa de Procesamiento Distribuido (ETL Avanzado):** Limpieza, enmascaramiento criptográfico de datos y extracción de características de estacionalidad temporal mediante **Apache Spark (PySpark)** en **Databricks**.
4. **Capa de Análisis y Visualización:** Monitoreo continuo de KPIs estratégicos (Ticket Promedio, Tasa de Cancelación, Ingresos) y segmentación RFM mediante dashboards interactivos.
5. **Capa de Predicción (Forecasting):** Componente de Machine Learning supervisado enfocado en la proyección del *Profit* mediante el entrenamiento competitivo de algoritmos de regresión.

---

## 🔒 Alineamiento con Normativas Internacionales de Seguridad

Para garantizar la protección de los datos masivos procesados en la nube, el entorno tecnológico fue diseñado bajo los lineamientos de dos estándares globales:

*   **ISO/IEC 20546 (Big Data — Framework y Requisitos de Arquitectura):** Se audita y garantiza la *Seguridad en Tránsito (Cifrado)* de extremo a extremo. Toda la comunicación entre los clusters de procesamiento distribuido y el almacenamiento cloud viaja estrictamente cifrada a través de protocolos **SSL/TLS** (`ssl_mode: REQUIRED`).
*   **ISO/IEC 27001 (Sistemas de Gestión de Seguridad de la Información):** Se asegura la *Privacidad de los Datos* en la capa ETL mediante técnicas de anonimización irreversible. El identificador transaccional de los usuarios (`id`) es enmascarado utilizando la función criptográfica **SHA-256** de PySpark.

---

## ⚙️ Tecnologías Utilizadas
*   **Lenguajes de Programación:** Python, SQL (MySQL Dialect).
*   **Procesamiento y Frameworks:** Apache Spark (PySpark), Pandas, Scikit-Learn, XGBoost.
*   **Infraestructura Cloud y MLOps:** Databricks (Serverless Compute), Aiven Cloud (Managed MySQL), MLflow.

---

## 📈 Rendimiento y Comparativa de Modelos
El componente de analítica predictiva puso a competir el algoritmo base desarrollado en la primera unidad frente a una arquitectura avanzada de ensamble en paralelo, evaluando su precisión a través de métricas estándar de la ciencia de datos (MAE, RMSE, $R^2$):

| Módulo Predictivo | Algoritmo / Framework | MAE | RMSE | Coef. Determinación ($R^2$) | Estado de Despliegue |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Modelo Base (U1)** | Random Forest (Scikit-Learn) | 212.07 | 315.58 | **0.6069** | Prototipo Local |
| **Modelo Avanzado (U2)** | XGBoost Random Forest (Nativo) | 229.81 | 347.89 | **0.5223** | **Version 1 (Ready)** |

### Conclusión Analítica:
El algoritmo de **Random Forest tradicional (Scikit-Learn)** retiene una mayor capacidad predictiva sobre las utilidades netas del negocio. Sin embargo, la implementación de la API nativa de **XGBoost** demostró una velocidad de cómputo y escalabilidad vertical drásticamente superior para entornos de Big Data masivos, además de ser la única arquitectura compatible con las políticas estrictas de firmas de metadatos exigidas para producción.

---

## 🌐 Gobernanza del Ciclo de Vida del Modelo (MLflow)
La gestión, auditoría y empaquetado del modelo ganador se centralizó mediante la plataforma **MLflow** en Databricks:
*   **Auditoría de Hiperparámetros:** Ingesta y registro automático (`mlflow.autolog()`) de los 37 parámetros teóricos del modelo para garantizar el control analítico.
*   **Model Signatures:** Inyección de una firma de metadatos explícita (`infer_signature`) para validar los tipos de esquema de entrada/salida ante el catálogo global (**Unity Catalog**).
*   **Model Registry:** Registro exitoso del artefacto bajo el estado **`Version 1 (Ready)`**, dejando el ecosistema cloud completamente empaquetado y preparado para funcionar como una API productiva de inferencia.
