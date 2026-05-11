# Análisis NLP de reseñas — Loveholidays

Proyecto de **Natural Language Processing** aplicado a reseñas reales de Trustpilot del sector *Travel & Vacation*. Combina análisis de sentimiento, topic modeling y benchmarking competitivo para extraer insights accionables de negocio. Práctica final de módulo del **Máster en Data Science e Inteligencia Artificial**.

> 📊 **[Ver presentación ejecutiva (PDF)](./presentacion-analisis-loveholidays.pdf)** · 📓 **[Notebook completo](./analisis-loveholidays.ipynb)**

---

## Pregunta de negocio

¿Qué piensan los clientes de **loveholidays.com**, sobre qué temas hablan, y cómo se sitúa la empresa frente a su competencia directa (TUI, Jet2 Holidays, Lastminute)? El análisis responde a cuatro preguntas concretas:

1. ¿Son las reseñas mayoritariamente positivas o negativas?
2. ¿De qué temas hablan los clientes?
3. ¿Cuál es el sentimiento asociado a cada tema?
4. ¿Dónde están las áreas de mejora prioritarias?

---

## Resultados principales

| Métrica | Loveholidays | TUI | Jet2 | Lastminute |
|---|---|---|---|---|
| **Polaridad media** | +0.177 | +0.152 | +0.189 | +0.098 |
| **% Positivas** | 63% | 58% | 65% | 51% |
| **% Negativas** | 6% | 9% | 5% | 12% |

→ **Loveholidays se sitúa por encima de la media del sector** en sentimiento positivo, aunque ligeramente por detrás de Jet2 Holidays.

---

## Metodología

### 1. Limpieza y preparación del texto

Construcción de un pipeline de limpieza propio que normaliza caracteres especiales, elimina ruido (URLs, emojis problemáticos, espacios redundantes) y filtra reseñas por sector para asegurar comparabilidad entre competidores.

### 2. Análisis de sentimiento

Aplicación de **TextBlob** sobre el corpus limpio para calcular polaridad por reseña, clasificación tripartita (positiva/neutra/negativa) y agregación por empresa para benchmarking competitivo.

### 3. Topic modeling

Extracción de los temas latentes mediante **NMF (Non-negative Matrix Factorization)** sobre una matriz **TF-IDF**. Se identifican cinco temas dominantes en las reseñas:

| Topic | Palabras clave | Reseñas |
|---|---|---|
| **Reserva Online** | book, booking, website, easy, process | 42 |
| **Alojamiento** | hotel, room, stay, clean, bed | 26 |
| **Experiencia General** | holiday, great, love, trip, time | 17 |
| **Precio / Reembolsos** | price, money, refund, pay, cost | 10 |
| **Atención al Cliente** | service, customer, staff, help, call | 5 |

### 4. Cruce sentimiento × topic

El verdadero valor del análisis surge al combinar ambas dimensiones. La polaridad media por topic revela qué temas son fortalezas comunicables y cuáles requieren acción:

| Topic | Polaridad | Evaluación |
|---|---|---|
| Reserva Online | +0.184 | 🟢 Fortaleza |
| Experiencia General | +0.169 | 🟢 Fortaleza |
| Alojamiento | +0.102 | 🟡 Oportunidad |
| Precio / Reembolsos | +0.085 | 🟡 Oportunidad |
| Atención al Cliente | +0.045 | 🟡 Oportunidad |

**Umbrales de decisión:**
- 🟢 Fortaleza (pol > 0.15): mantener y comunicar activamente
- 🟡 Oportunidad (pol 0–0.15): margen de mejora
- 🔴 Crítico (pol < 0): acción inmediata

---

## Stack técnico

`Python` · `Pandas` · `NumPy` · `scikit-learn` (`TfidfVectorizer`, `NMF`) · `TextBlob` · `WordCloud` · `Matplotlib` · `Seaborn` · `Jupyter`

---

## Dataset

**Trustpilot — Reseñas del sector Travel & Vacation**
🔗 https://www.trustpilot.com

El dataset no se incluye en este repositorio por su tamaño (>100MB). Las reseñas proceden de Trustpilot y han sido recopiladas con fines académicos para este análisis.

---

## Conclusiones de negocio

1. **Posición competitiva favorable.** Loveholidays está por encima de la media del sector en polaridad de sentimiento, lo que valida la calidad percibida del servicio
2. **Las fortalezas son operativas.** El proceso de reserva online y la experiencia general del viaje son los aspectos mejor valorados — son activos comunicables en campañas
3. **Las debilidades están en post-venta.** Atención al cliente y gestión de reembolsos concentran la mayor parte de la fricción
4. **Recomendación accionable:** priorizar inversión en atención al cliente (CX post-venta) y construir mensajes de marketing alrededor de las fortalezas en reserva online

---

## Próximos pasos

- **Modelos transformer** (BERT/RoBERTa multilingüe) para sentimiento más preciso que TextBlob
- **Aspect-Based Sentiment Analysis (ABSA)** para detectar sentimiento sobre aspectos concretos dentro de una misma reseña
- **Análisis temporal** de la evolución del sentimiento por topic para detectar tendencias y picos negativos
- **Dashboard interactivo** (Power BI / Streamlit) que el equipo de CX pueda consultar de forma continuada

---

## Autor

**Alejandro Rodríguez de la Rosa**
Marketing · Data Science · IA
📧 alejandrorodriguezdelarosa@gmail.com
🔗 [LinkedIn](https://www.linkedin.com/in/alejandro-rodríguez-de-la-rosa-015956301)

