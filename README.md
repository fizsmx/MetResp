# MetResp — Calculadora y Suite de Métodos Numéricos

Aplicación web profesional e interactiva orientada al cálculo científico, ingeniería y docencia universitaria. Resuelve ejercicios de métodos numéricos generando el desarrollo analítico y numérico completo paso a paso, emulando la rigurosidad de un procedimiento en cuaderno de notas.

Desarrollado por Fisbert | Repositorio: [github.com/fizsmx/MetResp](https://github.com/fizsmx/MetResp) | Licencia MIT

---

## Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Características Principales](#características-principales)
- [Herramientas Integradas](#herramientas-integradas)
  - [Calculadora Científica](#calculadora-científica)
  - [Entrada Inteligente](#entrada-inteligente)
- [Catálogo de Métodos Numéricos](#catálogo-de-métodos-numéricos)
  - [Raíces de Ecuaciones](#raíces-de-ecuaciones)
  - [Sistemas de Ecuaciones Lineales](#sistemas-de-ecuaciones-lineales)
  - [Interpolación](#interpolación)
  - [Integración Numérica](#integración-numérica)
  - [Ecuaciones Diferenciales Ordinarias](#ecuaciones-diferenciales-ordinarias)
  - [Ajuste de Curvas](#ajuste-de-curvas)
- [Instrucciones de Uso](#instrucciones-de-uso)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Licencia y Créditos](#licencia-y-créditos)

---

## Descripción General

MetResp es un entorno de cómputo numérico concebido para estudiantes, docentes y profesionales del área de ciencias e ingeniería. A diferencia de las calculadoras estándar que proporcionan únicamente la respuesta final, la plataforma desglosa cada iteración, sustitución matemática, evaluación de derivadas, operaciones matriciales y cálculos de error aproximado relativo porcentual ($e_a$).

La plataforma se ejecuta de manera totalmente local en el navegador del usuario, prescindiendo de servidores de procesamiento de fondo o instalaciones complejas.

---

## Características Principales

- Procedimiento paso a paso estilo cuaderno: Exposición explícita de fórmulas base, sustitución de variables en cada paso, operaciones algebraicas intermedias y criterios de parada.
- Modalidad de visualización dual: Alternancia entre modo detallado (demostración completa de cada cálculo) y modo compacto (tablas sinópticas de convergencia rápida).
- Gráficas de convergencia y funciones: Representación gráfica interactiva del comportamiento de las funciones, interpolaciones, ajustes y curvas de convergencia del error relativo con Chart.js.
- Exportación múltiple: Generación de reportes limpios en texto plano (.txt) y exportación directa a documento imprimible o PDF.
- Historial persistente en almacenamiento local: Registro automático de ejercicios evaluados mediante Web Storage API (localStorage), permitiendo recuperar estados y datos previos sin pérdida de información.
- Sistema de temas: Interfaz conmutable entre modo oscuro y modo claro con persistencia de configuración del usuario.
- Interfaz adaptable (Responsive Design): Adaptada para resoluciones de escritorio, computadoras portátiles, tabletas y teléfonos móviles.
- Rigurosidad tipográfica y estética: Formato matemático estructurado, limpio y sin elementos distractores o emojis, adecuado para presentaciones académicas formales.

---

## Herramientas Integradas

### Calculadora Científica

Módulo de cómputo auxiliar integrado para operaciones intermedias y soporte de cálculo continuo:
- Operaciones aritméticas estándar, exponenciación y radicación.
- Funciones trigonométricas directas, inversas e hiperbólicas (seno, coseno, tangente, etc.).
- Funciones logarítmicas de base natural ($\ln$) y base decimal ($\log_{10}$).
- Operaciones de memoria de registro: suma a memoria (M+), resta de memoria (M-), recuperación (MR) y borrado (MC).
- Historial de expresiones y resultados reutilizables en un clic.

### Entrada Inteligente

Motor de análisis léxico y sintáctico que interpreta enunciados de problemas en lenguaje natural:
- Detección automática del algoritmo objetivo (por ejemplo, identificación de palabras clave como "Newton", "Bisección", "Euler", "Gauss").
- Extracción automatizada de parámetros: funciones matemáticas $f(x)$, condiciones iniciales ($x_0$, $y_0$), intervalos de búsqueda $[a, b]$, tamaño de paso ($h$), tolerancias porcentuales y número límite de iteraciones.
- Precarga inmediata en el módulo correspondiente con ejecución asistida.

---

## Catálogo de Métodos Numéricos

El software cuenta con 16 métodos numéricos distribuidos en 6 áreas disciplinarias del análisis numérico.

### Raíces de Ecuaciones

Solución de ecuaciones algebraicas y trascendentes no lineales de la forma $f(x) = 0$.

#### 1. Newton-Raphson
Método abierto con convergencia cuadrática cerca de la raíz, fundamentado en la aproximación por recta tangente:
$$x_{i+1} = x_i - \frac{f(x_i)}{f'(x_i)}$$
- Incluye cálculo simbólico y numérico automático de la primera derivada $f'(x)$.
- Estimación del error relativo porcentual: $e_a = \left| \frac{x_{i+1} - x_i}{x_{i+1}} \right| \times 100\%$.

#### 2. Bisección
Método cerrado o de reducción de intervalos que aplica el Teorema del Valor Intermedio (Bolzano) para funciones continuas donde $f(a) \cdot f(b) < 0$:
$$x_r = \frac{a + b}{2}$$
- Verificación estricta de cambio de signo en cada subintervalo.
- Convergencia monótona garantizada con reducción del intervalo a la mitad por paso.

#### 3. Punto Fijo
Método de aproximaciones sucesivas que reformula $f(x) = 0$ bajo la estructura equivalente $x = g(x)$:
$$x_{i+1} = g(x_i)$$
- Análisis de la condición suficiente de convergencia: $|g'(x)| < 1$ en la vecindad de la solución.
- Monitoreo y alerta de posibles patrones divergentes.

#### 4. Método de la Secante
Método abierto que aproxima la pendiente de la derivada mediante diferencias finitas a partir de dos estimaciones previas $x_{i-1}$ y $x_i$:
$$x_{i+1} = x_i - \frac{f(x_i)(x_i - x_{i-1})}{f(x_i) - f(x_{i-1})}$$
- No requiere el cálculo explícito ni analítico de la derivada de la función.

#### 5. Regla Falsa (Regula Falsi)
Método cerrado que une los puntos extremos $(a, f(a))$ y $(b, f(b))$ mediante una recta secante para calcular el corte con el eje horizontal:
$$x_r = \frac{a \cdot f(b) - b \cdot f(a)}{f(b) - f(a)}$$
- Mantiene la garantía de convergencia de un método cerrado, incrementando usualmente la rapidez de convergencia respecto a la bisección pura.

---

### Sistemas de Ecuaciones Lineales

Solución de sistemas lineales simultáneos de orden $n \times n$ expresados en forma matricial $A \mathbf{x} = \mathbf{b}$.

#### 6. Gauss-Jordan
Método directo de eliminación que reduce la matriz aumentada $[A \mid \mathbf{b}]$ a la forma escalonada reducida por filas $[I \mid \mathbf{x}]$:
- Normalización del pivote: $R_i \leftarrow \frac{R_i}{a_{ii}}$.
- Eliminación de coeficientes superiores e inferiores: $R_k \leftarrow R_k - a_{ki} R_i$ para todo $k \neq i$.
- Diagnóstico automático de compatibilidad: solución única, infinitas soluciones (sistema indeterminado) o contradicción (sistema incompatible).

#### 7. Jacobi
Método iterativo que descompone la matriz de coeficientes en componentes diagonal, triangular inferior y superior ($A = D - L - U$):
$$x_i^{(k+1)} = \frac{1}{a_{ii}} \left( b_i - \sum_{j \neq i} a_{ij} x_j^{(k)} \right)$$
- Los valores de todas las incógnitas se renuevan en bloque al completar la iteración.
- Evaluación de la condición de convergencia por diagonal estrictamente dominante.

#### 8. Gauss-Seidel
Método iterativo acelerado que utiliza de forma inmediata los valores recién calculados dentro del mismo ciclo iterativo:
$$x_i^{(k+1)} = \frac{1}{a_{ii}} \left( b_i - \sum_{j < i} a_{ij} x_j^{(k+1)} - \sum_{j > i} a_{ij} x_j^{(k)} \right)$$
- Presenta una tasa de convergencia sustancialmente más veloz que el esquema de Jacobi estándar.

---

### Interpolación

Determinación de polinomios que pasan de forma exacta por un conjunto de $n+1$ nodos dados $(x_0, y_0), (x_1, y_1), \dots, (x_n, y_n)$.

#### 9. Interpolación de Lagrange
Construcción directa del polinomio interpolador mediante combinaciones lineales ponderadas de polinomios base:
$$P_n(x) = \sum_{i=0}^{n} y_i L_i(x), \quad L_i(x) = \prod_{\substack{j=0 \\ j \neq i}}^{n} \frac{x - x_j}{x_i - x_j}$$
- No requiere resolver sistemas de ecuaciones algebraicas.
- Detalle explícito de cada producto parcial $L_i(x)$ y sustitución de coordenadas.

#### 10. Interpolación de Newton (Diferencias Divididas)
Formulación polinómica basada en coeficientes progresivos obtenidos mediante la tabla de diferencias divididas:
$$P_n(x) = f[x_0] + \sum_{k=1}^{n} f[x_0, x_1, \dots, x_k] \prod_{j=0}^{k-1} (x - x_j)$$
Donde la diferencia dividida de orden $k$ se define recursivamente como:
$$f[x_i, \dots, x_{i+k}] = \frac{f[x_{i+1}, \dots, x_{i+k}] - f[x_i, \dots, x_{i+k-1}]}{x_{i+k} - x_i}$$
- Generación completa de la matriz triangular de diferencias divididas.

---

### Integración Numérica

Aproximación de la integral definida $I = \int_a^b f(x) \, dx$ a través de fórmulas de cuadratura de Newton-Cotes.

#### 11. Regla del Trapecio
Aproximación lineal simple y compuesta en $n$ subintervalos de ancho $h = \frac{b - a}{n}$:
$$I \approx \frac{h}{2} \left[ f(x_0) + 2 \sum_{i=1}^{n-1} f(x_i) + f(x_n) \right]$$
- Ilustración de las alturas nodales y el cálculo de la suma ponderada de trapecios.

#### 12. Simpson 1/3
Aproximación por segmentos parabólicos de segundo orden para intervalos subdivididos en un número par de partes ($n$ par):
$$I \approx \frac{h}{3} \left[ f(x_0) + 4 \sum_{i=1,3,5}^{n-1} f(x_i) + 2 \sum_{j=2,4,6}^{n-2} f(x_j) + f(x_n) \right]$$
- Error de truncamiento local de orden $O(h^5)$ y orden global $O(h^4)$.

#### 13. Simpson 3/8
Aproximación cúbica de tercer orden diseñada para particiones donde el número de subintervalos $n$ es múltiplo de 3:
$$I \approx \frac{3h}{8} \left[ f(x_0) + 3 \sum_{\substack{i=1 \\ i \neq 3k}}^{n-1} f(x_i) + 2 \sum_{k=1}^{\frac{n}{3}-1} f(x_{3k}) + f(x_n) \right]$$
- Aplicable de forma independiente o combinada con la regla de Simpson 1/3.

---

### Ecuaciones Diferenciales Ordinarias

Aproximación numérica de problemas de valor inicial (PVI) de la forma $\frac{dy}{dx} = f(x, y)$ con $y(x_0) = y_0$.

#### 14. Método de Euler
Esquema explícito de primer orden basado en la aproximación por serie de Taylor truncada en la derivada de primer orden:
$$y_{i+1} = y_i + h \cdot f(x_i, y_i)$$
- Seguimiento visual de la propagación del paso $h$ y la evolución de la pendiente local.

#### 15. Runge-Kutta de 4to Orden (RK4)
Método de alta precisión y estabilidad que promedia cuatro evaluaciones de pendiente ponderadas dentro de cada intervalo:
$$y_{i+1} = y_i + \frac{h}{6} (k_1 + 2k_2 + 2k_3 + k_4)$$
Donde:
$$k_1 = f(x_i, y_i)$$
$$k_2 = f\left(x_i + \frac{h}{2}, \; y_i + \frac{h}{2} k_1\right)$$
$$k_3 = f\left(x_i + \frac{h}{2}, \; y_i + \frac{h}{2} k_2\right)$$
$$k_4 = f(x_i + h, \; y_i + h k_3)$$
- Procedimiento exhaustivo con el cálculo explícito de $k_1, k_2, k_3, k_4$ por iteración.

---

### Ajuste de Curvas

Modelado estadístico y funcional mediante el método de mínimos cuadrados para conjuntos de datos experimentales $(x_i, y_i)$.

#### 16. Mínimos Cuadrados (Lineal y Polinomial)
Minimización de la suma de los residuos al cuadrado $S_r = \sum_{i=1}^n (y_i - \hat{y}_i)^2$:
- **Regresión Lineal ($y = a_0 + a_1 x$):**
  Resolución del sistema normal:
  $$\begin{cases} n a_0 + a_1 \sum x_i = \sum y_i \\ a_0 \sum x_i + a_1 \sum x_i^2 = \sum x_i y_i \end{cases}$$
- **Regresión Polinomial de grado $m$ ($y = a_0 + a_1 x + \dots + a_m x^m$):**
  Construcción y resolución del sistema matricial normal generalizado:
  $$\begin{bmatrix} n & \sum x & \dots & \sum x^m \\ \sum x & \sum x^2 & \dots & \sum x^{m+1} \\ \vdots & \vdots & \ddots & \vdots \\ \sum x^m & \sum x^{m+1} & \dots & \sum x^{2m} \end{bmatrix} \begin{bmatrix} a_0 \\ a_1 \\ \vdots \\ a_m \end{bmatrix} = \begin{bmatrix} \sum y \\ \sum xy \\ \vdots \\ \sum x^m y \end{bmatrix}$$
- Métricas estadísticas de bondad de ajuste:
  - Coeficiente de determinación $R^2$.
  - Coeficiente de correlación $r$.
  - Error estándar de la estimación $S_{y/x}$.

---

## Instrucciones de Uso

1. **Ejecución Local:**
   Abra el archivo `index.html` en cualquier navegador web moderno (Google Chrome, Mozilla Firefox, Microsoft Edge, Safari u Opera). No es necesaria la configuración de un servidor local (Apache, Nginx, Node.js) ni la compilación previa de dependencias.

2. **Resolución Asistida (Entrada Inteligente):**
   - Inserte el texto completo del enunciado en la caja de texto superior.
   - Presione el botón **Analizar y Resolver**.
   - El sistema identificará el método adecuado, extraerá las variables y redirigirá a la pestaña correspondiente mostrando la resolución completa.

3. **Resolución Manual por Categoría:**
   - Seleccione la pestaña correspondiente al método numérico deseado.
   - Complete los campos requeridos (función, puntos, valores iniciales, tolerancias o tablas de datos).
   - Presione el botón **Resolver**.

4. **Visualización y Exportación:**
   - Examine el desglose paso a paso en el área de resultados.
   - Utilice los botones de acción para alternar entre el modo detallado y compacto, generar gráficas de convergencia, o exportar el reporte en formato de texto plano o PDF.

---

## Tecnologías Utilizadas

- **HTML5 semántico:** Estructura de documentos estandarizada, accesible y modular.
- **CSS3 moderno:** Diseño visual profesional con CSS Custom Properties (variables), efectos de desenfoque translúcido (Glassmorphism), maquetación mediante CSS Grid y Flexbox.
- **JavaScript Vanilla (ES6+):** Lógica matemática y manipulación de interfaz sin dependencias de frameworks pesados (Zero Framework Overhead).
- **[Chart.js](https://www.chartjs.org/):** Renderizado dinámico sobre lienzo (Canvas) de curvas funcionales, puntos de muestreo y gráficos de dispersión/error.
- **[math.js](https://mathjs.org/):** Motor de análisis simbólico y evaluación numérica segura de funciones analíticas y expresiones matemáticas complejas.
- **Google Fonts:** Fuentes tipográficas seleccionadas para máxima legibilidad técnica: *Space Grotesk* (titulares e interfaz) y *JetBrains Mono* (expresiones matemáticas, fórmulas y matrices).

---

## Estructura del Proyecto

```text
MetResp/
├── index.html        Archivo principal y completo de la aplicación (HTML, CSS y JS)
├── README.md         Documentación técnica y académica del proyecto
└── LICENSE           Términos de la licencia de código abierto MIT
```

---

## Licencia y Créditos

Este proyecto se distribuye bajo la licencia de código abierto **MIT License**. Consulte el archivo [LICENSE](LICENSE) para mayores detalles sobre términos de uso, modificación y distribución.

- **Autor:** Fisbert
- **Repositorio Oficial:** [https://github.com/fizsmx/MetResp](https://github.com/fizsmx/MetResp)
