# Trabajo Práctico 3 - Aprendizaje No Supervisado

## Realizado por: Sofía Quiroz Valencia

## 1. Descripción del proyecto

Este proyecto desarrolla un análisis de aprendizaje no supervisado utilizando el conjunto de datos **Wholesale Customers**, disponible en Kaggle. La base contiene información de 440 clientes mayoristas y sus gastos anuales en diferentes categorías de productos.

El propósito es identificar grupos de clientes con comportamientos de compra similares mediante técnicas de reducción de dimensionalidad y agrupamiento.

## 2. Objetivo

Aplicar técnicas de aprendizaje no supervisado para identificar patrones de consumo entre clientes mayoristas, utilizando el Análisis de Componentes Principales (PCA), la selección de variables y el algoritmo K-means.

## 3. Descripción de los datos

El conjunto de datos contiene ocho variables:

- **Channel:** canal de venta del cliente.
- **Region:** región del cliente.
- **Fresh:** gasto anual en productos frescos.
- **Milk:** gasto anual en productos lácteos.
- **Grocery:** gasto anual en productos de supermercado.
- **Frozen:** gasto anual en productos congelados.
- **Detergents_Paper:** gasto anual en detergentes y productos de papel.
- **Delicassen:** gasto anual en productos delicatessen.

Para el análisis se utilizaron seis variables numéricas relacionadas con los gastos de los clientes. Las variables Channel y Region se excluyeron porque representan categorías y no cantidades de consumo.

## 4. Metodología

El desarrollo del trabajo se realizó en las siguientes etapas:

1. **Exploración y preparación de datos:** revisión de la estructura del conjunto de datos y verificación de valores faltantes.
2. **Estandarización:** aplicación de StandardScaler para llevar las variables a una escala comparable.
3. **Análisis de Componentes Principales (PCA):** reducción de dimensionalidad y análisis de la varianza explicada.
4. **Selección de variables:** análisis de correlación para identificar características redundantes. Se eliminó Detergents_Paper debido a su correlación de 0.925 con Grocery.
5. **Agrupamiento con K-means:** aplicación del algoritmo utilizando los datos originales, los dos componentes principales y las cinco variables seleccionadas.
6. **Evaluación:** comparación de los resultados mediante el método del codo, la inercia y el coeficiente Silhouette, evaluando valores de K entre 2 y 6.

## 5. Principales resultados

El análisis PCA permitió identificar que los dos primeros componentes explican el **72.46 % de la variabilidad total** de los datos.

En la selección de variables se encontró una correlación de 0.925 entre Grocery y Detergents_Paper, por lo que se eliminó la segunda variable para reducir la redundancia.

Posteriormente, se compararon los tres enfoques mediante K-means. Los mejores resultados fueron:

| Enfoque | K | Silhouette Score |
|---|---:|---:|
| Datos originales | 3 | 0.5483 |
| PCA (2 componentes) | 2 | 0.6362 |
| Selección de variables | 2 | 0.6277 |

La mejor combinación fue **PCA con dos componentes y K=2**, que obtuvo un coeficiente Silhouette de 0.6362.

## 6. Conclusiones

Los resultados muestran que las técnicas de reducción de dimensionalidad pueden facilitar la identificación de patrones de compra en los clientes mayoristas. Entre los enfoques evaluados, PCA presentó el mejor resultado, al obtener una mayor separación entre los grupos.

El ejercicio permitió comparar diferentes alternativas de agrupamiento y reconocer la importancia de preparar y transformar los datos antes de aplicar un algoritmo de aprendizaje no supervisado.

