# 📊 Modelos de Clasificación para Captación de Clientes Potenciales

**Autor:** Rodrigo Pinedo  
**Fecha:** 12 de abril del 2025  

---

## 🎯 Objetivo del Proyecto

- Predecir si un cliente se suscribirá a un depósito a plazo.
- Maximizar **recall** para identificar la mayor cantidad de clientes potenciales.
- Evitar variables con data leakage para garantizar realismo.

---

## 🎯 Metodología

![metodología](image-3.png)

<img src="../src/image-3.png" alt="curva ROC" width="60%">
---

## 📁 Dataset

- Fuente: Bank Marketing Dataset (versión ajustada)
- 20 variables predictoras después del preprocesamiento
- Variable objetivo: `y` → 1 = sí, 0 = no
- Distribución desbalanceada: ~11% clase positiva (`y=1`)

---

## 🛠️ Preprocesamiento

- Eliminación de `duration` (variable posterior al evento)
- Agrupación de edad (`age_bin`) y campaña (`campaign`)
- Índice económico creado vía PCA (`economic_index`)
- One-hot encoding de variables categóricas
- Balanceo con `scale_pos_weight`, sin SMOTE

---

## 🧠 Modelos Evaluados

| Modelo              | Técnica de Balanceo          |
|---------------------|------------------------------|
| Random Forest       | `class_weight='balanced'`    |
| LightGBM            | `scale_pos_weight`           |
| Logistic Regression | `class_weight='balanced'`    |
| XGBoost             | `scale_pos_weight`           |

---

## 📊 Métricas de Evaluación

| Modelo         | Recall (y=1) | Precision | F1-score | ROC AUC |
|----------------|--------------|-----------|----------|---------|
| LightGBM       | **0.6171**   | **0.3849**| **0.4741**| **0.7914** |
| XGBoost        | 0.6289       | 0.3601    | 0.4579   | 0.7922  |
| Random Forest  | 0.5786       | 0.3990    | 0.4723   | 0.7852  |
| Logistic Reg.  | 0.6813       | 0.2571    | 0.3733   | 0.7642  |

---

## 📈 Curva ROC

*Comparación visual de la capacidad discriminativa de cada modelo.*  
(Acá insertás tu gráfico)

![alt text](image.png)

---

## 📉 Curva Precision-Recall

*Trade-off entre recall y precision por modelo.*  

![alt text](image-1.png)

---

## 📌 Importancia de Variables – LightGBM

Top 15 variables más influyentes:  

![alt text](image-2.png)

---

## ✅ Conclusión

> Se recomienda utilizar **LightGBM** por los siguientes motivos:

- Mantiene un **recall competitivo** en el top 3.
- Obtiene la **mejor F1-score** y precision entre los modelos.
- Tiene un **ROC AUC alto (0.7914)**, indicando excelente discriminación.
- Es rápido, interpretable y portable a producción.

---

## 🔜 Siguientes pasos

- Modelo guardado como `.joblib` y `.pkl` en `/models`
- Listo para integración en una API o dashboard
- Ajuste de umbral posible para diferentes escenarios comerciales

---

## ❓ Preguntas

Gracias por tu atención.
