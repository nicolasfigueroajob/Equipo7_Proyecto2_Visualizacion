# Equipo 7 · Proyecto 2: Recetas de Bienestar (World Happiness Report 2024)

**Autores:** Joshua Trujillo y Nicolás Figueroa  
**Curso:** Visualización I · Universidad Externado de Colombia · Octubre 2026  
**Audiencia Técnica:** Unidad de Investigación Comparativa y Análisis de Políticas de Bienestar (PNUD / Banco Mundial)

---

## 1. Escenario Analítico y Pregunta de Investigación

El presente informe constituye un análisis exploratorio reproducible desarrollado con Python a partir del conjunto de datos oficial del *World Happiness Report 2024*. Su propósito es evaluar empíricamente la combinación de indicadores que conforman la evaluación de vida de los países y analizar críticamente el componente que escapa a los modelos cuantitativos estándar.

### Pregunta Analítica
> **¿Qué «recetas» de bienestar predominan entre los países con mayor y menor evaluación de vida según el WHR 2024, y en qué medida el componente no explicado (Distopía + residual) altera o cuestiona dichas recetas?**

> **Nota de Cautela Inferencial:** Todas las relaciones examinadas corresponden estrictamente a **asociaciones empíricas observables** y no deben interpretarse como relaciones de causalidad directa.

---

## 2. Hallazgos Analíticos Centrales

1. **La «Receta» es Homogénea (Diferencia de Nivel, no de Composición):**  
   Los países del Tercil Superior y del Tercil Inferior comparten la misma estructura porcentual básica: el **PIB per cápita (34%–36%)** y el **Apoyo Social (27%–29%)** concentran más del **63%** de la receta explicada en ambos extremos. La disparidad en el bienestar subjetivo obedece a una brecha en la magnitud absoluta alcanzada en los mismos pilares estructurales, y no a modelos de desarrollo con recetas distintas.

2. **Disociación del Residuo $D$ (Efecto de Agrupamiento):**  
   El componente no explicado $D$ (*Distopía + residual*) varía entre $-0.07$ y $3.00$ pts. Mientras que a nivel global exhibe una correlación moderada con la evaluación de vida ($r = +0.53$), el análisis desagregado por tercil demuestra que:
   * En el **Tercil Superior ($r = +0.06$)** y **Tercil Medio ($r = +0.01$)**, la correlación es **nula**; el residuo fluctúa libremente y la jerarquía la determinan los factores explicados.
   * En el **Tercil Inferior ($r = +0.61$)**, la correlación es **fuerte y positiva**; el desplome del residuo ante crisis agudas o guerras civiles es el factor determinante que precipita a una nación al fondo del escalafón global.

3. **La Ventaja Latinoamericana y Casos Atípicos (Tukey):**  
   * **América Latina:** Países como Costa Rica ($D=2.33$), México ($D=2.44$), El Salvador ($D=2.42$) y Uruguay ($D=1.89$) se ubican sistemáticamente por encima de la diagonal de balance esperada, respaldados por un colchón de capital social comunitario y familiar.
   * **Atípico Alto:** **Venezuela ($D = 3.00, L = 5.61$)** supera el límite superior de Tukey; su evaluación se sostiene casi exclusivamente en el componente no explicado.
   * **Atípicos Bajos:** Países severamente penalizados bajo el límite inferior de Tukey ($D < 0.81$): **Líbano ($D = -0.07$)**, **Afganistán ($0.67$)**, **Sri Lanka ($0.01$)** y **Egipto ($0.35$)**.

---

## 3. Entregables Oficiales en este Repositorio

El repositorio contiene el paquete completo de entregables exigidos por la rúbrica de evaluación:

| Archivo | Descripción | Formato |
|---|---|:---:|
| **[Equipo7_Proyecto2_Notebook.ipynb](Equipo7_Proyecto2_Notebook.ipynb)** | **Notebook de Jupyter reproducible y 100% ejecutado:** Flujo integral con 4 visualizaciones estáticas en Seaborn (con su análisis escrito) y 2 visualizaciones interactivas en Plotly (con dropdown de dimensiones e inspección multidimensional). | `.ipynb` |
| **[Equipo7_Proyecto2_Resumen.pdf](Equipo7_Proyecto2_Resumen.pdf)** | **Informe Ejecutivo Oficial:** Documento condensado de **exactamente 3 páginas** con síntesis analítica, tabla comparativa por tercil y recomendaciones para organismos internacionales *(fuente editable en [Resumen.md](Equipo7_Proyecto2_Resumen.md))*. | `.pdf` |
| **[Equipo7_Proyecto2_Anexo_IA.pdf](Equipo7_Proyecto2_Anexo_IA.pdf)** | **Anexo Técnico de Uso de IA:** Documento de **exactamente 1 página** con declaración de herramientas, prompts clave (incluyendo paleta accesible Okabe-Ito) y supervisión crítica del equipo *(fuente editable en [Anexo_IA.md](Equipo7_Proyecto2_Anexo_IA.md))*. | `.pdf` |
| **[Equipo7_Proyecto2_Interactivos.html](Equipo7_Proyecto2_Interactivos.html)** | **Visualizaciones Interactivas Plotly Autónomas:** Archivo HTML con los gráficos de dispersión multidimensional y ranking Top-15 listos para visualización directa en cualquier navegador web. | `HTML` |
| **[data/WHR24_Data_Figure_2.1.xls](data/WHR24_Data_Figure_2.1.xls)** | **Datos Oficiales Originales:** Archivo oficial descargado directamente de la SDSN (World Happiness Report 2024, Figure 2.1). | `.xls` |
| **[requirements.txt](requirements.txt)** | **Entorno de Reproducibilidad:** Lista de librerías y versiones exactas para la reproducción íntegra del análisis. | `txt` |

---

## 4. Instrucciones de Reproducción Local

Para ejecutar el notebook desde el inicio y replicar todos los resultados:

```bash
# 1. Clonar este repositorio
git clone https://github.com/nicolasfigueroajob/Equipo7_Proyecto2_Visualizacion.git
cd Equipo7_Proyecto2_Visualizacion

# 2. Instalar dependencias requeridas
pip install -r requirements.txt

# 3. Iniciar Jupyter Notebook / JupyterLab
jupyter notebook Equipo7_Proyecto2_Notebook.ipynb
```
