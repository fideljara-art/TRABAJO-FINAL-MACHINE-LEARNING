# Reducción de Dimensionalidad: Teorema de Johnson-Lindenstrauss

Este proyecto explora el *Teorema de Johnson-Lindenstrauss*, un resultado fundamental en el análisis de datos de alta dimensión que justifica la proyección de puntos a espacios de menor dimensión preservando casi por completo las distancias euclídeas.

## Objetivo del Proyecto

El objetivo principal es validar empíricamente el Teorema de Johnson-Lindenstrauss mediante simulaciones numéricas, comparando implementaciones en Python. Se busca demostrar que es posible reducir drásticamente la dimensión de un conjunto de datos con una distorsión controlada ($\varepsilon$), analizando las cotas teóricas y el comportamiento de las proyecciones aleatorias.

## Descripción del Método

El Teorema de Johnson-Lindenstrauss establece que para cualquier $0<\varepsilon<1$, $n\geq 1$ y $k\geq \frac{48}{\varepsilon^2}\log n$, $U\sim\mathcal{N}(0_{k\times d},1)$ y un conjunto de $n$ puntos en $\mathbb{R}^d$ puede ser mapeado a un espacio $\mathbb{R}^k$ (con $k \ll d$) mediante una proyección $T_{U(\omega)}$ tal que para todo par de puntos $\mathbf{x}_{i},\mathbf{x}_{j}$:

$$\mathbb{P}[\forall i,j:(1-\varepsilon)\|\mathbf{x}_{i}-\mathbf{x}_{j}\|\leq\|T_{U(\omega)}(\mathbf{x}_{i})-T_{U(\omega)}(\mathbf{x}_{j})\|\leq(1+\varepsilon)\|\mathbf{x}_{i}-\mathbf{x}_{j}\|]\geq 1-\frac{1}{n}.$$

La implementación sigue estos pasos:
1. **Generación de Datos:** Se crean matrices de datos sintéticos $X$ (ej. $150 \times 20,000$) usando una distribución uniforme $U(0, 1)$.
2. **Proyección Aleatoria:** Se utiliza una matriz de proyección $\Phi$ con valores de una distribución normal $N(0, 1/k)$.
3. **Verificación de Distancias:** Se calculan las distancias en el espacio original y en el proyectado para verificar la proporción de pares que cumplen la cota de distorsión.
4. **Visualización:** Generación de gráficos que muestran la razón entre la distancia proyectada y la original.

## Estructura del Repositorio

- `python/`: Scripts de simulación en Python (`tabla51.py`, `figura21.py`).
- `reporte/`: Documentación técnica y académica en $\LaTeX$.
- `figuras/`: Resultados visuales de las simulaciones.

## Instrucciones de Ejecución

### Requisitos

- **Python 3**: Requiere `numpy` y `matplotlib`.

### Ejecución en Python

Para generar la tabla de validación (utiliza procesamiento en paralelo):
```bash
python python/tabla51.py
```

Para generar la visualización de distorsión de distancias:
```bash
python python/figura21.py
```

## Obtención de Datos

Los datos utilizados en las simulaciones son **generados sintéticamente** por los propios scripts. No se requieren archivos de datos externos. Las dimensiones y parámetros ($\varepsilon$, $n$, $d$) están definidos en las variables iniciales de cada archivo fuente, permitiendo ajustar la complejidad del experimento.
