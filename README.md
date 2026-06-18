# Análisis Comparativo de Clustering Lineal y No Lineal

## 📋 Descripción del Proyecto

Este proyecto evalúa y compara el rendimiento de tres algoritmos de clustering —**K-Means**, **DBSCAN** y **Spectral Clustering**— en tres conjuntos de datos con diferentes características geométricas:

- **Iris**: Dataset clásico (150 muestras, 4 características, 3 clases)
- **Moons**: Dataset sintético (300 muestras, 2 características, 2 lunas entrelazadas)
- **Circles**: Dataset sintético (500 muestras, 2 características, 2 círculos concéntricos)

El objetivo es determinar qué modelos son de naturaleza lineal y cuáles pueden capturar estructuras no lineales, así como identificar los hiperparámetros críticos para cada algoritmo.

## 🎯 Objetivos

- Entrenar K-Means, DBSCAN y Spectral Clustering en cada dataset
- Optimizar hiperparámetros mediante búsqueda en cuadrícula
- Evaluar con métricas externas: **ARI** y **V-Measure**
- Evaluar con métricas internas: **Silhouette Score**, **Davies-Bouldin Index** y **Elbow Method**
- Identificar la naturaleza (lineal/no lineal) de cada modelo
- Determinar hiperparámetros críticos para el entrenamiento exitoso

## 📊 Resultados Principales

### Naturaleza de los Modelos

| Modelo | Naturaleza | Fundamento |
|--------|-----------|------------|
| **K-Means** | Lineal | Fronteras hiperplanos; asume clústeres convexos |
| **DBSCAN** | No Lineal | Basado en densidad; detecta formas arbitrarias |
| **Spectral Clustering** | No Lineal | Basado en grafos/espectro; captura estructuras no convexas |

### Mejor Modelo por Dataset

| Dataset | Mejor Modelo | ARI | V-Measure | Conclusión |
|---------|--------------|-----|-----------|------------|
| **Iris** | Spectral Clustering | 0.6451 | 0.6895 | Captura relaciones no lineales entre especies |
| **Moons** | DBSCAN | 1.0000 | 1.0000 | Sigue curvaturas de las lunas por densidad |
| **Circles** | DBSCAN / Spectral | 1.0000 | 1.0000 | Ambos capturan estructuras circulares no convexas |

### Hiperparámetros Críticos

| Modelo | Hiperparámetro Crítico | Impacto |
|--------|----------------------|---------|
| **K-Means** | `n_clusters` | Define número de clústeres; incorrecto → agrupación subóptima |
| **DBSCAN** | `eps`, `min_samples` | Definen densidad y forma; incorrectos → ruido o fusión de clústeres |
| **Spectral Clustering** | `n_clusters`, `gamma` | `gamma` controla escala del kernel RBF; incorrecto → pérdida de estructura no lineal |

## 🛠️ Requisitos

```bash
pip install -r requirements.txt
