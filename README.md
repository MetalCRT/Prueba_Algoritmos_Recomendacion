# 📊 Prueba de Algoritmos de Recomendación

Se utilizaron **LightGCN** y **BPR** sobre el dataset **MovieLens-100k**.

---

## 🛠️ Explicación del procedimiento

1. Se instalaron los paquetes de Python necesarios:  
   - [`jupyter`](https://jupyter.org/)  
   - [`RecBole`](https://recbole.io/)  

2. Se crearon parámetros de prueba en un archivo `test.yaml` para definir las métricas de evaluación.

3. Se ejecutaron las pruebas con el algoritmo **LightGCN**:
   - **Prueba 1:** Métricas *NDCG* y *Precision*.
   - **Prueba 2:** Métrica *RMSE*.

4. Se repitieron las pruebas con **BPR** usando los mismos parámetros para comparar resultados.

---

## 📚 Explicación e interpretación

### 🔹 Algoritmos
- **LightGCN**: Algoritmo de recomendación basado en _embeddings_, es decir, vectores en una matriz. Su propósito es entrenar una función de puntuación, que le asigne mejores puntajes a pares de usuario-objeto que sean buenas recomendaciones, y peores puntajes en caso contrario.   
- **BPR** (*Bayesian Personalized Ranking*): Optimiza preferencias relativas entre pares de interacciones (i, j), aprendiendo que si un usuario prefiere un ítem *i* frente a otro *j*, se ajusten las preferencias del modelo para reflejarlo.

---

### 🔹 Métricas de evaluación
- **RMSE**: Mide el error medio al predecir calificaciones.  
  Ejemplo: Un RMSE de `0.5` significa un error promedio de media estrella (en escala 1–5). Menor valor = mejor resultado.
- **Precision**: Proporción de resultados relevantes sobre todos los resultados.
- **NDCG**: Métrica que nos indica la comparación del ranking de objetos, con el obtenido por el modelo (es decir, mientras más cercano al 1 es esta métrica, más cerca está la prueba del ranking ideal de las películas del dataset).  

---

## 📈 Resultados

- **LightGCN** tuvo mejor desempeño en RMSE (dado que mientras menor puntaje, menos error en esta métrica).  
- **BPR** tuvo mejor desempeño en métricas de NDCG y Precision.

![Resultados](https://github.com/MetalCRT/Prueba_Algoritmos_Recomendacion/blob/main/Resultados.png)  

📌 **Interpretación:**  
- Al ser un dataset relativamente pequeño, se observa que **BPR** tiene mejor desempeño en las métricas de _ranking_ (*Precision* y *NDCG*), es decir, el ordenamiento de las películas por usuario. Por otro lado, **LightGCN** tiene mejor desempeño en *RMSE*, lo que indica que tiene menos error al predecir los *ratings* exactos de los objetos.
- Esto implica un **trade-off** al elegir algoritmo:
  - Si importa más recomendar películas adecuadas: **BPR**
  - Si importa más predecir con exactitud la puntuación: **LightGCN**
