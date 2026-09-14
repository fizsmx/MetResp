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

MetResp es un entorno de cómputo numérico concebido para estudiantes, docentes y profesionales del área de ciencias e ingeniería. A diferencia de las calculadoras estándar que proporcionan únicamente la respuesta final, la plataforma desglosa cada iteración, sustitución matemática, evaluación de derivadas, operaciones matriciales y cálculos de error aproximado relativo porcentual.

La plataforma se ejecuta de manera totalmente local en el navegador del usuario, prescindiendo de servidores de procesamiento de fondo o instalaciones complejas.

---

## Características Principales

- Procedimiento paso a paso estilo cuaderno: Exposición explícita de fórmulas base, sustitución de variables en cada paso, operaciones algebraicas intermedias y criterios de parada.
- Explicación Teórica: Cada método incluye un bloque teórico explicativo con las fórmulas clave, los criterios de convergencia y las condiciones de uso, apoyando el proceso educativo.
- Ejemplos Predefinidos: Incorporación de conjuntos de ejemplos listos para cargar en cada método (incluidos los puntos de las tablas), facilitando la comprensión y validación de resultados.
- Verificación razonada de todos los métodos: Cada cálculo termina con un bloque que explica **por qué** esa comprobación valida el resultado (la propiedad matemática que debe cumplirse), muestra la comprobación numérica y emite una conclusión. Las pruebas son propias de cada familia: sustitución en la función original y cambio de signo en los métodos de raíces; residuos |Ax−b| y dominancia diagonal en los sistemas; L·U = A en la factorización LU; paso por los puntos y ΣLᵢ(x) = 1 en interpolación; continuidad C⁰, C¹, C² y condiciones naturales en splines; contraste con una integral refinada y con la misma regla al duplicar n en integración; comparación con una solución de referencia y comprobación de la pendiente f(x,y) en las EDO; y ortogonalidad de los residuos (condición de mínimo) en mínimos cuadrados.
- Modalidad de visualización dual: Alternancia entre modo detallado (demostración completa de cada cálculo) y modo compacto (tablas sinópticas de convergencia rápida).
- Gráficas dinámicas y explicadas: Cada método publica una o varias vistas intercambiables mediante pestañas (función y raíz, convergencia del error, área aproximada, error según n, solución y error de las EDO, residuos del ajuste, curvatura de los splines, evolución de las incógnitas en los métodos iterativos, entre otras). Todas llevan título, ejes rotulados, escala numérica real y tooltips interactivos, y debajo se incluye un pie que explica qué se está viendo y cómo interpretarlo.
- Cálculo en tiempo real: En la calculadora de interpolación lineal el resultado, la gráfica y el desarrollo se actualizan automáticamente conforme se introducen los datos, sin necesidad de pulsar ningún botón.
- Exportación múltiple: Generación de reportes limpios en texto plano (.txt) y exportación directa a documento imprimible o PDF.
- Historial persistente en almacenamiento local: Registro automático de ejercicios evaluados mediante Web Storage API (localStorage), permitiendo recuperar estados y datos previos sin pérdida de información.
- Sistema de temas: Interfaz conmutable entre modo oscuro y modo claro con persistencia de configuración del usuario.
- Interfaz adaptable (Responsive Design): Adaptada para resoluciones de escritorio, computadoras portátiles, tabletas y teléfonos móviles.
- Rigurosidad tipográfica y estética: Formato matemático estructurado, limpio y sin elementos distractores, adecuado para presentaciones académicas formales.

---

## Herramientas Integradas

### Calculadora Científica

Módulo de cómputo auxiliar integrado para operaciones intermedias y soporte de cálculo continuo:
- Operaciones aritméticas estándar, exponenciación y radicación.
- Funciones trigonométricas directas, inversas e hiperbólicas.
- Funciones logarítmicas de base natural y base decimal.
- Operaciones de memoria de registro.
- Historial de expresiones y resultados reutilizables en un clic.

### Entrada Inteligente

Motor de análisis léxico y sintáctico que interpreta enunciados de problemas en lenguaje natural:
- Detección automática del algoritmo objetivo.
- Extracción automatizada de parámetros: funciones matemáticas, condiciones iniciales, intervalos de búsqueda, tamaño de paso, tolerancias porcentuales y número límite de iteraciones.
- Precarga inmediata en el módulo correspondiente con ejecución asistida.

---

## Catálogo de Métodos Numéricos

El software cuenta con 20 métodos numéricos distribuidos en 6 áreas disciplinarias del análisis numérico.

### Raíces de Ecuaciones

Solución de ecuaciones algebraicas y trascendentes no lineales de la forma $f(x) = 0$.

#### 1. Newton-Raphson
Método abierto con convergencia cuadrática cerca de la raíz, fundamentado en la aproximación por recta tangente.

#### 2. Bisección
Método cerrado o de reducción de intervalos que aplica el Teorema del Valor Intermedio (Bolzano) para funciones continuas.

#### 3. Punto Fijo
Método de aproximaciones sucesivas que reformula $f(x) = 0$ bajo la estructura equivalente $x = g(x)$.

#### 4. Método de la Secante
Método abierto que aproxima la pendiente de la derivada mediante diferencias finitas a partir de dos estimaciones previas.

#### 5. Regla Falsa (Regula Falsi)
Método cerrado que une los puntos extremos mediante una recta secante para calcular el corte con el eje horizontal.

---

### Sistemas de Ecuaciones Lineales

Solución de sistemas lineales simultáneos de orden $n \times n$.

#### 6. Gauss-Jordan
Método directo de eliminación que reduce la matriz aumentada a la forma escalonada reducida por filas.

#### 7. Jacobi
Método iterativo que descompone la matriz de coeficientes en componentes diagonal, triangular inferior y superior.

#### 8. Gauss-Seidel
Método iterativo acelerado que utiliza de forma inmediata los valores recién calculados dentro del mismo ciclo iterativo.

#### 9. Factorización LU
Método directo que descompone la matriz del sistema en el producto de una matriz triangular inferior L y una triangular superior U, siendo altamente eficiente para resolver múltiples sistemas con la misma matriz de coeficientes.

---

### Interpolación

Estimación de valores intermedios a partir de datos conocidos, desde la recta entre dos puntos hasta polinomios que pasan de forma exacta por un conjunto de puntos.

#### 10. Interpolación Lineal
Estimación de un valor intermedio a partir de dos puntos conocidos suponiendo comportamiento rectilíneo entre ellos. La calculadora permite nombrar libremente ambas variables, introducir los dos puntos conocidos y el valor conocido (X ó Y) del tercer punto: el valor faltante se obtiene de forma automática mientras se escribe, junto con la gráfica de la recta y el desarrollo completo del cálculo (incrementos, pendiente, despeje, sustitución numérica, ecuación de la recta y verificación por colinealidad). El sistema distingue además entre interpolación y extrapolación según la ubicación del punto solicitado.

#### 11. Interpolación de Lagrange
Construcción directa del polinomio interpolador mediante combinaciones lineales ponderadas de polinomios base.

#### 12. Interpolación de Newton (Diferencias Divididas)
Construcción del polinomio Pn(x) = a0 + a1(x−x0) + a2(x−x0)(x−x1) + ... + an(x−x0)(x−x1)...(x−xn−1), cuyos coeficientes son las diferencias divididas de la primera fila de la tabla. El desarrollo muestra los datos, la fórmula general, el cálculo de cada diferencia dividida con su fracción sustituida, la tabla completa con los coeficientes aj resaltados, el polinomio en forma de Newton y en forma estándar simplificada, la evaluación opcional en un valor de x y la gráfica de comprobación. La verificación confirma que el polinomio reproduce exactamente cada punto dado.

#### 13. Splines Cúbicos
Interpolación segmentada mediante polinomios de tercer grado unidos con condiciones de suavidad continua hasta su segunda derivada, evitando el fenómeno de oscilación de Runge en los extremos.

---

### Integración Numérica

Aproximación de integrales definidas a través de diversas fórmulas.

#### 14. Regla del Trapecio
Aproximación lineal simple y compuesta en subintervalos.

#### 15. Simpson 1/3
Aproximación por segmentos parabólicos de segundo orden para intervalos subdivididos en un número par de partes.

#### 16. Simpson 3/8
Aproximación cúbica de tercer orden diseñada para particiones donde el número de subintervalos es múltiplo de 3.

#### 17. Romberg
Técnica de mejora de precisión que combina repetidamente el método del trapecio mediante extrapolación de Richardson, logrando resultados de alta exactitud computacional.

---

### Ecuaciones Diferenciales Ordinarias

Aproximación numérica de problemas de valor inicial.

#### 18. Método de Euler
Esquema explícito de primer orden basado en la aproximación por serie de Taylor truncada.

#### 19. Runge-Kutta de 4to Orden (RK4)
Método de alta precisión y estabilidad que promedia cuatro evaluaciones de pendiente ponderadas dentro de cada intervalo.

---

### Ajuste de Curvas

Modelado estadístico y funcional para conjuntos de datos experimentales.

#### 20. Mínimos Cuadrados
Minimización de la suma de los residuos al cuadrado para ajustar de forma óptima un modelo lineal o polinomial, analizando posteriormente el nivel de correlación y la calidad general del ajuste.

---

## Instrucciones de Uso

1. **Ejecución Local:**
   Abra el archivo `index.html` en cualquier navegador web moderno. No es necesaria la configuración de un servidor local.

2. **Carga de Ejemplos:**
   Cada método cuenta con botones rápidos para poblar el formulario con ejemplos prediseñados, útiles para pruebas rápidas y propósitos didácticos.

3. **Resolución Asistida:**
   Inserte el texto completo del enunciado en la caja de texto superior y el sistema ajustará automáticamente los parámetros y el método idóneo.

4. **Visualización y Verificación:**
   Examine el desglose paso a paso en el área de resultados, confirme la precisión matemática a través del bloque de verificación final, o revise el diagrama generado dinámicamente.

---

## Tecnologías Utilizadas

- **HTML5 semántico**
- **CSS3 moderno**
- **JavaScript Vanilla (ES6+)**
- **Chart.js**
- **math.js**
- **Google Fonts**

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

Este proyecto se distribuye bajo la licencia de código abierto **MIT License**. Consulte el archivo LICENSE para mayores detalles sobre términos de uso, modificación y distribución.

- **Autor:** Fisbert
- **Repositorio Oficial:** [https://github.com/fizsmx/MetResp](https://github.com/fizsmx/MetResp)
