# Equipo 7 · Informe Ejecutivo: Recetas de Bienestar en el World Happiness Report 2024

**Autores:** Joshua Trujillo y Nicolás Figueroa  
**Curso:** Visualización I · Universidad Externado de Colombia · Octubre 2026  
**Audiencia Técnica:** Unidad de Investigación Comparativa y Análisis de Políticas de Bienestar (PNUD / Banco Mundial)

---

## 1. Escenario Analítico, Audiencia y Pregunta de Investigación

El análisis internacional del bienestar subjetivo suele verse restringido por enfoques unidimensionales centrados exclusivamente en el crecimiento económico. Organismos multilaterales como el PNUD y el Banco Mundial requieren marcos interpretativos que permitan desglosar cómo interactúan los determinantes materiales e institucionales y evaluar qué proporción del bienestar observado escapa a los modelos cuantitativos formales.

### Pregunta Analítica
> **¿Qué «recetas» de bienestar predominan entre los países con mayor y menor evaluación de vida según el World Happiness Report 2024, y en qué medida el componente no explicado (Distopía + residual) altera o cuestiona dichas recetas?**

**Principio de Cautela Inferencial:** En conformidad con el diseño metodológico del WHR 2024, los resultados aquí expuestos corresponden a **asociaciones empíricas observables** y no deben interpretarse como relaciones de causalidad directa.

---

## 2. Descripción de los Datos y Metodología de Preparación

### Fuente Oficial
Se utilizó el archivo oficial obligatorio: `WHR24_Data_Figure_2.1.xls` ($N = 143$ países), publicado por la Red de Soluciones para el Desarrollo Sostenible (SDSN). Se verificó la consistencia aditiva exacta de la ecuación del reporte:
$$\text{Ladder Score } (L) = \sum_{j=1}^{6} c_j + D$$
donde $\sum c$ representa la suma de las seis contribuciones explicadas (PIB per cápita, Apoyo Social, Esperanza de Vida, Libertad para Decidir, Generosidad y Percepción de Corrupción) y $D$ es el componente de *Distopía + residual*. Tras excluir tres registros con información incompleta, la muestra analítica consolidada cuenta con **140 países**.

### Estratificación Empírica por Terciles
Para comparar de forma objetiva los extremos de bienestar sin recurrir a umbrales subjetivos, la muestra se estratificó en tres cuantiles de tamaño equilibrado ($\approx 47$ países por grupo):
* **Tercil Inferior ($L \le 5.17$ pts):** Países en situación de vulnerabilidad y bajo bienestar.
* **Tercil Medio ($5.17 < L \le 6.19$ pts):** Franja de transición e ingreso medio.
* **Tercil Superior ($L > 6.19$ pts):** Países con alta evaluación de vida.

### Regla Formal de Atípicos (Tukey)
Sobre el componente no explicado $D$, se calcularon los límites intercuartílicos:
$$\text{Lím. Inferior} = Q_1 - 1.5 \times IQR = 0.81 \text{ pts}, \quad \text{Lím. Superior} = Q_3 + 1.5 \times IQR = 2.62 \text{ pts}$$

---

## 3. Principales Hallazgos Analíticos

### A. La Arquitectura de la «Receta» es Homogénea (Diferencia de Nivel, no de Composición)
El hallazgo central del análisis comparativo revela que los países del Tercil Superior y del Tercil Inferior comparten prácticamente la misma estructura porcentual de receta explicada:
* El **PIB per cápita** aporta entre el **33.8% y el 35.6%** de la suma explicada en ambos grupos.
* El **Apoyo Social** aporta entre el **27.3% y el 28.6%**.
* Sumados con la **Esperanza de Vida** (~13%), estas tres variables concentran más del **75%** de la receta explicada en cualquier país del mundo.
* Por el contrario, la *Generosidad* y la *Percepción de Corrupción* tienen una ponderación agregada reducida (< 5% cada una).

**Implicación técnica:** La brecha entre los países prósperos y los rezagados no se debe a que utilicen modelos o recetas de desarrollo con ingredientes cualitativamente distintos, sino a una profunda **disparidad en la magnitud absoluta** de los mismos factores básicos (el aporte del PIB y del soporte social en el tercil superior duplica al del tercil inferior).

### B. El Componente No Explicado ($D$) y la Disociación Intra-Tercil
El residuo $D$ presenta una mediana global de $1.74$ pts, pero oscila entre $-0.07$ y $3.00$ pts. Al analizar su relación con $L$, se descubrió un fenómeno metodológico crítico:
* **A nivel global:** Se observa una correlación positiva moderada ($r = +0.53$).
* **Al desagregar por terciles (Efecto de agrupamiento):**
  * En el **Tercil Superior ($r = +0.06$)** y en el **Tercil Medio ($r = +0.01$)**, la correlación es **completamente nula**. En países de ingreso medio y alto, el residuo fluctúa independientemente del ranking; las variaciones de bienestar dependen de los componentes explicados.
  * En el **Tercil Inferior ($r = +0.61$)**, la correlación es **fuerte y positiva**. En la franja más vulnerable del mundo, el residuo es el factor determinante: el colapso del componente no explicado es lo que precipita a un país hacia el fondo absoluto de la escala.

### C. Patrones Geográficos y Países Atípicos
* **La Ventaja Residual Latinoamericana:** Naciones como Costa Rica ($D=2.33$), México ($D=2.44$), El Salvador ($D=2.42$) y Uruguay ($D=1.89$) se sitúan sistemáticamente por encima de la diagonal esperada. Factores socioculturales, lazos comunitarios y redes de parentesco generan niveles de bienestar subjetivo muy superiores a los previstos por sus variables macroeconómicas.
* **Atípico Alto:** **Venezuela ($D = 3.00, L = 5.61$)** es el único caso sobre el límite superior de Tukey. Su evaluación se mantiene en el tercil medio sustentada casi exclusivamente en el componente no explicado.
* **Atípicos Bajos:** Países con severas penalizaciones residuales por debajo del límite de Tukey: **Líbano ($D = -0.07$)**, **Afganistán ($D = 0.67$)**, **Sri Lanka ($D = 0.01$)** y **Egipto ($D = 0.35$)**, donde crisis agudas y estrés psicosocial deprimen el bienestar drásticamente.

---

## 4. Conclusiones, Limitaciones y Recomendaciones de Política

1. **Prioridad en el Soporte Social e Institucional Básico:** Dado que el PIB y el apoyo social concentran más del 60% de la receta en todos los niveles, las políticas públicas no pueden concebir el desarrollo social como un subproducto secundario del crecimiento económico; ambos deben avanzar de manera simultánea.
2. **Reconocimiento del Capital Social Intangible:** Los organismos internacionales deben incorporar formalmente la medición de redes comunitarias y bienestar relacional en sus modelos estándar para comprender la resiliencia en regiones como América Latina.
3. **Limitaciones:** El estudio reconoce que $D$ combina la constante hipotética del país distópico (1.71 pts) con el residuo del modelo de regresión. Se sugiere para futuras investigaciones desagregar estos componentes mediante microdatos a nivel individual.
