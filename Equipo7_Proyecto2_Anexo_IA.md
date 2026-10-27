# Equipo 7 · Anexo Técnico: Declaración de Uso de Inteligencia Artificial

**Curso:** Visualización I · Universidad Externado de Colombia · Octubre 2026  
**Integrantes:** Joshua Trujillo y Nicolás Figueroa  
**Proyecto:** Proyecto 2 — Recetas de Bienestar (World Happiness Report 2024)

---

### 1. Herramientas Utilizadas y Propósito General

* **Herramientas de IA empleadas:** Antigravity IDE (asistente de código basado en Google Gemini 3.8 Flash).
* **Propósito analítico y técnico:**  
  1. Asistencia en la estructuración modular del código de visualización en Python (`Seaborn` y `Plotly`).
  2. Implementación algorítmica de la regla de detección de atípicos de Tukey sobre el residuo $D$.
  3. Selección y verificación de paletas de color con contraste accesible para personas con daltonismo (ColorBrewer / Okabe-Ito).

---

### 2. Prompts Clave Empleados

#### Prompt 1: Paleta de Colores Accesible (Requisito Obligatorio)
> *"Diseña una paleta de 3 colores accesible para personas con daltonismo (siguiendo estándares de Okabe-Ito / ColorBrewer) para clasificar los terciles de bienestar (Inferior, Medio y Superior). Evita esquemas tipo semáforo (verde-rojo) y garantiza alto contraste sobre fondo blanco."*
* **Código adoptado:**
  ```python
  PALETA_TERCILES = {
      "Inferior": "#D55E00",  # Borde naranja rojizo accesible (Okabe-Ito)
      "Medio": "#999999",     # Gris neutro de contraste intermedio
      "Superior": "#0072B2"   # Azul accesible (Okabe-Ito)
  }
  ```

#### Prompt 2: Menú Desplegable Dinámico en Plotly (Top-15)
> *"Escribe el código para un gráfico de barras horizontales interactivo con Plotly Express / Graph Objects que use 'updatemenus' con un menú desplegable (dropdown) para alternar dinámicamente entre las 6 dimensiones del WHR 2024, coloreando las barras según el tercil del país y agregando tooltips con el Ladder Score."*

#### Prompt 3: Límites de Tukey para el Componente No Explicado ($D$)
> *"Escribe una función en Pandas/NumPy que calcule los límites de Tukey ($Q_1 - 1.5 \times IQR$ y $Q_3 + 1.5 \times IQR$) sobre la variable 'Distopía + residual' para clasificar formalmente a los países en atípicos altos, típicos y atípicos bajos."*

---

### 3. Reflexión Crítica y Validación Humana del Equipo

El equipo humano ejerció un control estricto sobre cada sugerencia y línea de código generada, rechazando y corrigiendo propuestas automatizadas que carecían de rigor:

1. **Corrección de la Falacia de Agregación (Correlación Global vs. Intra-Tercil):**  
   Inicialmente, el asistente trazó una única regresión global ($r = 0.53$), sugiriendo que el residuo crecía de forma uniforme con el bienestar. El equipo auditó el resultado y exigió la desagregación por terciles, descubriendo que la correlación es prácticamente nula en el tercil medio ($r = 0.01$) y superior ($r = 0.06$), y que se concentra con fuerza en el tercil inferior ($r = 0.61$). Se rediseñó el Gráfico 4 en dos paneles para reflejar esta realidad analítica.
2. **Depuración de Errores de Renderizado:**  
   Se identificó y corrigió un error en el parámetro de tamaño de burbuja de Plotly (`px.scatter`), el cual colapsaba ante el valor negativo de Líbano ($D = -0.07$), aplicando un reescalado inferior acotado sin alterar el dato original.
3. **Control Inferencial Estricto:**  
   El equipo revisó minuciosamente cada interpretación y conclusión del informe para erradicar cualquier lenguaje causal, garantizando que todos los hallazgos se formulen como asociaciones empíricas observables.
