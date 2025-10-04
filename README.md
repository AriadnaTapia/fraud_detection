# 💳 Credit Card Fraud Detection

Un proyecto de **Machine Learning** para detectar transacciones fraudulentas en tarjetas de crédito.  
Se compararon distintos algoritmos para evaluar cuál ofrece el mejor balance entre **precisión y sensibilidad (recall)** en un dataset altamente desbalanceado.

---

## 📊 Contexto

El fraude con tarjetas de crédito representa **millones de pérdidas anuales** en la industria financiera.  
El reto principal en este problema es que los fraudes son extremadamente raros:  
en este dataset público (Kaggle) **menos del 0.17% de las transacciones son fraudulentas**.

👉 El objetivo fue desarrollar un modelo de clasificación que logre **detectar la mayor cantidad de fraudes posible (alto recall)** sin generar demasiadas falsas alarmas.

---

## 🔍 Metodología

1. **Exploración de datos (EDA):**
   - 284,807 transacciones totales.
   - Solo 492 casos de fraude (0.17%).
   - No se encontraron valores nulos; se eliminaron duplicados.

2. **Preprocesamiento:**
   - Escalado automático de `V1...V28` (PCA).
   - Normalización de `Amount` y `Time` cuando fue necesario.
   - Ajuste de desbalance con `class_weight='balanced'`.

3. **Entrenamiento de modelos:**
   - 🌲 Random Forest  
   - ⚡ LightGBM  
   - 🐱 CatBoost  

4. **Evaluación:**
   - ROC-AUC  
   - PR-AUC (más relevante en dataset desbalanceado).  
   - Classification Report.  
   - Matriz de confusión.

---

## 📈 Resultados

| Modelo        | ROC-AUC | PR-AUC | Precisión (fraudes) | Recall (fraudes) | F1-score |
|---------------|:-------:|:------:|:-------------------:|:----------------:|:--------:|
| 🌲 Random Forest | 0.966 | 0.819 | 0.947 | 0.747 | 0.835 |
| ⚡ LightGBM      | 0.973 | 0.818 | 0.899 | 0.747 | 0.816 |
| 🐱 CatBoost      | **0.977** | 0.792 | 0.675 | **0.810** | 0.737 |

🔹 **Random Forest:** más conservador, casi sin falsos positivos pero menor recall.  
🔹 **LightGBM:** balance intermedio y rápido en entrenamiento.  
🔹 **CatBoost:** mejor recall (81%), reduciendo fraudes no detectados aunque con más falsas alarmas.

---

## 💡 Conclusiones

- Todos los modelos alcanzaron un rendimiento sobresaliente (**ROC-AUC > 0.96**).  
- **CatBoost** resultó el más adecuado si la prioridad es **detectar fraudes** (maximizar recall).  
- En un entorno real, **ajustar el umbral de decisión** puede ayudar a equilibrar precisión y recall según las necesidades del negocio.  

👉 El proyecto demuestra cómo enfrentar problemas de **clases altamente desbalanceadas** en la práctica.

---

## 🚀 Próximos pasos

- Ajuste dinámico de umbrales para optimizar recall/precisión.  
- Probar oversampling (SMOTE) y detección no supervisada (Isolation Forest, Autoencoders).  
- Implementar el modelo en un flujo de **detección en tiempo real**.

---

## 🛠️ Tecnologías utilizadas

- Python  
- Pandas, NumPy  
- Scikit-learn  
- LightGBM, CatBoost  
- Matplotlib, Seaborn  

---

## 📂 Recursos

- 📊 Dataset: [Credit Card Fraud Detection (Kaggle)](https://www.kaggle.com/mlg-ulb/creditcardfraud)  
- 📓 Notebook: *incluido en este repositorio*  
- ✨ Autor: *Ariadna Rosas Tapia*

---
