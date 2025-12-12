# Predicción de Fallas en Redes Eléctricas y Asistente Técnico Inteligente (Agentic RAG)

**Hecho por:**
* Ismael Cortes Ramirez
* Juan Camilo Giraldo Jimenez

Este proyecto implementa una solución de Inteligencia Artificial híbrida para la gestión de activos de distribución eléctrica. Combina modelos de Deep Learning Tabular (**TabNet**) para la predicción de indisponibilidad (UITI) con un sistema de **Agentes Inteligentes (RAG)** para la consulta automatizada de normativa técnica.

## ⚡ 1. Descripción del Problema
Las interrupciones en el servicio de energía eléctrica generan pérdidas económicas y afectan la calidad de vida. El objetivo de este estudio es:
1.  **Predecir** el índice de indisponibilidad (UITI) basándose en variables históricas, climáticas y de infraestructura.
2.  **Diagnosticar** automáticamente la zona más crítica de la red.
3.  **Recomendar** acciones de mantenimiento basadas en la normativa técnica oficial mediante un asistente de IA.

## 📚 2. Recursos y Estado del Arte
Este desarrollo toma como referencia la metodología propuesta en el estado del arte sobre gestión de activos en redes eléctricas.

* **📄 Paper de Referencia:** [Paper_AI_CHECUNAL.pdf]([(https://github.com/amalvarezme/AprendizajeMaquina/blob/main/Paper_AI_CHECUNAL.pdf)])
* **💾 Base de Datos:** [PowerGrid Assets ML Dataset en Kaggle]([(https://www.kaggle.com/datasets/cristiancamiloo/powergrid-assets-ml-dataset/data/data/data)])
* **📘 Documentación Técnica:** [Reglamento de Redes Aéreas MT](UBICADO_EN_EL_REPOSITORIO)

## 🛠️ 3. Metodología Implementada

### A. Modelo Predictivo (TabNet)
Se utilizó **TabNet** (Google Cloud AI), una arquitectura de aprendizaje profundo que utiliza mecanismos de atención secuencial.
* **Target:** UITI (Unavailability Index).
* **Estrategia:** Time-Aware Split (Entrenamiento con pasado, validación con futuro).

### B. Agentic RAG (Retrieval-Augmented Generation)
Se diseñó un sistema Multi-Agente orquestado con **LangChain** y **Google Flan-T5**:
1.  **Agente Analista:** Escanea los datos y detecta el circuito crítico (8629).
2.  **Agente Normativo:** Consulta una base vectorial (**FAISS**) creada a partir del manual técnico y responde preguntas sobre seguridad y materiales.

## 📊 4. Hallazgos Principales

### Importancia de Variables (Feature Importance)
El modelo TabNet reveló que las variables meteorológicas tienen un impacto superior a la antigüedad de los equipos.
<img width="727" height="488" alt="Feature Importance" src="https://github.com/user-attachments/assets/38a6a88b-94a5-46ee-81f6-d202170cb6f7" />


> **Conclusión:** La presión atmosférica y la velocidad del viento son los precursores más fuertes de fallas, sugiriendo que la mayoría de eventos son causados por condiciones climáticas exógenas.

## 🤖 5. Demostración del Sistema de Agentes

El sistema autónomo generó el siguiente diagnóstico y recomendaciones técnicas sin intervención humana:

<img width="1208" height="515" alt="Salida Agentes" src="https://github.com/user-attachments/assets/8760727a-3759-4883-aab9-ca216695e4dc" />


## 💻 6. Ejecución
El código completo se encuentra en el archivo `.ipynb` de este repositorio. Fue desarrollado y ejecutado en **Kaggle** para aprovechar la aceleración por GPU.

---
*Proyecto presentado para la asignatura de Teoria Aprendizaje de Máquina.*
