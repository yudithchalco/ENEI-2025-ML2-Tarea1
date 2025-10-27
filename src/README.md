# ENEI 2025 ML2

Este proyecto integra tres secciones correspondientes a la **Tarea 1**.

---

## Parte A: Clasificación de Tweets sobre Desastres
**Dataset:** disaster_tweets.csv  
**Objetivo:** clasificar si un tweet corresponde a un desastre real (1) o no (0).  
**Modelos aplicados:**
- Regresión Logística (con y sin regularización)
- Naive Bayes
- N-gramas (1 y 2)

**Resultados principales:**
- F1 promedio: 0.75  
- Mejor desempeño con Regresión Logística L2

**Conclusión:**  
El modelo logra buena precisión; la regularización y el preprocesamiento de texto son claves para evitar sobreajuste.


## Parte B: Máquinas de Vectores de Soporte (SVM)
**Objetivo:** estudiar el efecto del parámetro `C` en el sobreajuste.  
**Metodología:**
- Generación de datos linealmente separables  
- Entrenamiento con distintos valores de `C`  
- Comparación de accuracies (train, CV y test)

**Conclusión:**  
Valores pequeños de `C` generan subajuste (alto sesgo).  
Valores grandes producen sobreajuste (alta varianza).  
El mejor desempeño se obtuvo con `C` intermedio (1 a 10).


## Parte C: Árboles de Regresión - Dataset Carseats
**Dataset:** Carseats (paquete ISLP)  
**Objetivo:** predecir las ventas de asientos para niños en función de precio, ingreso y ubicación.  

**Resultados:**
- MSE árbol completo: 9.7227  
- MSE árbol podado (max_depth=4): 6.9183  
**Variables más influyentes:** ShelveLoc, Price, CompPrice, Advertising, Income.  

**Conclusión:**  
El árbol podado reduce la varianza y mejora la capacidad de generalización.  
Los factores más relevantes son la ubicación del producto y el precio.

---
- Chalco Cerezo Yudith Diana  
