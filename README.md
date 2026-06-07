# PCA Interactivo — Visualización de Componentes Principales

Aplicación web interactiva para explorar visualmente el **Análisis de Componentes Principales (ACP/PCA)** en datos bivariados. Desarrollada con [p5.js](https://p5js.org/) como recurso pedagógico para cursos de estadística, econometría y ciencia de datos.

🔗 **Demo en vivo**: [fcontiggiani.github.io/pca_app](https://fcontiggiani.github.io/pca_app)

---

## ¿Qué hace la app?

La pantalla se divide en dos zonas:

### Zona superior — Espacio de datos original (ℝ²)

Muestra 40 puntos generados con distribución gaussiana bivariada. Sobre ellos se proyectan una o dos componentes principales representadas como ejes lineales:

- **CP1** (azul oscuro): primera componente principal
- **CP2** (rojo): segunda componente, ortogonal a CP1

Las líneas punteadas muestran la proyección ortogonal de cada punto sobre el eje activo.

### Zona inferior — Espacio de componentes (puntajes)

Aparece al activar CP2. Muestra las **coordenadas de cada punto en el sistema CP1–CP2**, es decir, sus puntajes (*scores*) en cada componente. En este espacio:

- El eje horizontal representa los puntajes en CP1 (mayor varianza)
- El eje vertical representa los puntajes en CP2
- El coeficiente **r** indica la correlación entre puntajes: cuando CP1⊥CP2, `r ≈ 0`

---

## Controles

| Control | Descripción |
|---|---|
| **ALEATORIZAR** | Genera una nueva nube de puntos aleatoria |
| **OPTIMIZAR CP1** | Anima el eje hasta la dirección de máxima varianza proyectada |
| **FIJAR CP1 →** | Congela CP1 y activa la edición de CP2 (ortogonal por defecto) |
| **OPTIMIZAR CP2** | Anima CP2 al eje ortogonal a CP1 |
| **← EDITAR CP1** | Vuelve a la fase de edición de CP1 |
| **Proyecciones** | Muestra/oculta las líneas de proyección ortogonal |
| **Mantener ⊥** | Bloquea CP2 estrictamente perpendicular a CP1 al arrastrar |

**Interacción con el mouse:** arrastra sobre la zona superior del canvas para rotar el eje de la componente activa en tiempo real.

---

## Métricas mostradas

- **VAR**: varianza proyectada sobre el eje (media de los cuadrados de las proyecciones)
- **%**: fracción de la varianza total explicada por esa componente
- **Acumulado**: porcentaje acumulado CP1 + CP2 (en datos 2D, debería ser ≈ 100% cuando ambas son óptimas)
- **Ángulo CP1∧CP2**: ángulo entre los ejes (aparece ✓ cuando es ortogonal, ±1.5°)
- **r**: correlación de Pearson entre los puntajes de CP1 y CP2 (≈ 0 cuando son ortogonales)

---

## Fundamentos matemáticos

Dado un conjunto de $n$ puntos $\{(x_i, y_i)\}$ centrados en el origen, la **varianza proyectada** sobre un eje con dirección unitaria $\mathbf{d} = (\cos\theta, \sin\theta)$ es:

$$\text{Var}(\theta) = \frac{1}{n} \sum_{i=1}^{n} \langle \mathbf{p}_i, \mathbf{d} \rangle^2$$

La **primera componente principal** es el eje $\mathbf{d}^*$ que maximiza esta expresión, equivalente al autovector de la matriz de covarianza asociado al mayor autovalor. La app encuentra este máximo por búsqueda exhaustiva sobre $[0, \pi)$ en pasos de $0.01$ rad.

La **segunda componente principal** es ortogonal a la primera: $\mathbf{d}_2 \perp \mathbf{d}_1$. En datos bidimensionales, CP1 + CP2 capturan el 100% de la varianza.

---

## Tecnologías

- [p5.js](https://p5js.org/) v1.9.0 — renderizado del canvas y generación de datos
- HTML/CSS/JS puros — sin frameworks adicionales
- Compatible con GitHub Pages, Netlify, Vercel o cualquier hosting estático

---

## Usos sugeridos

- Clases introductorias de ACP/PCA en estadística o econometría
- Talleres de ciencia de datos y machine learning
- Material de apoyo para explicar la geometría de la reducción de dimensionalidad
- Demostraciones interactivas en presentaciones académicas

---

## Reconocimientos

Adaptado de la visualización original de **kynd**:
- Demo interactivo: [codepen.io/kynd/pen/dPOypvw](https://codepen.io/kynd/pen/dPOypvw)
- Referencia conceptual: [Principal Component Analysis — kynd](https://kyndinfo.notion.site/Principal-Component-Analysis-351019e814cf809f816eec61c3712b2a)

Las extensiones incluyen: segunda componente principal interactiva, gráfico de puntajes CP1–CP2, métricas de varianza explicada y correlación entre componentes, indicador de ortogonalidad, y etiquetas en español.

---

## Licencia

MIT — libre para usar, modificar y distribuir con atribución.
