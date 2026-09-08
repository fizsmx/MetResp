# 📐 MetResp — Calculadora de Métodos Numéricos

> **Aplicación web interactiva** que resuelve ejercicios de Métodos Numéricos mostrando el **procedimiento completo paso a paso**, como si lo escribieras en tu cuaderno.

<p align="center">
  <strong>Desarrollado por Fisbert</strong>
</p>

---

## ✨ Característica Principal: Entrada Inteligente

**Pega el enunciado completo de tu ejercicio** y la app lo analiza automáticamente:
- Detecta qué método usar (Newton-Raphson, Bisección, Punto Fijo, Gauss-Jordan)
- Extrae la función `f(x)`, valores iniciales, tolerancia e intervalos
- Rellena los campos y resuelve instantáneamente

Ejemplos de enunciados que puedes pegar:
```
Aplicar bisección para f(x) = e^(3x) - 4 en el intervalo (0,1) con error de 0.01
```
```
Usar Newton-Raphson en f(x) = e^x - 2 + x² con x₀ = 0 y tolerancia 0.01
```
```
Método punto fijo para f(x) = 2sen(x) - x, g(x) = 2sen(x), x₀ = 1.5, e = 0.01
```

---

## 🚀 Métodos Incluidos

### 1. Newton-Raphson
Encuentra raíces de ecuaciones no lineales `f(x) = 0`.
- **Fórmula:** x_{i+1} = x_i − f(x_i) / f'(x_i)
- Autocalcula la derivada si se omite
- Muestra cada evaluación, sustitución y cálculo de error

### 2. Bisección
Encuentra raíces por el método del intervalo medio.
- **Pasos:** I) Punto medio → II) Evaluaciones → III) Nuevo intervalo → IV) Error
- Validación automática de cambio de signo

### 3. Punto Fijo
Encuentra raíces usando una función de iteración `g(x)`.
- **Fórmula:** x_{i+1} = g(x_i)
- Detecta divergencia automáticamente

### 4. Gauss-Jordan
Resuelve sistemas de ecuaciones lineales por eliminación.
- Matrices desde **2×2 hasta 6×6**
- Entrada por **ecuaciones en texto** o por **matriz manual**
- Detecta: solución única, infinitas soluciones o sistema incompatible

---

## 🎨 Características de la Interfaz

| Característica | Descripción |
|---|---|
| 🧠 **Entrada inteligente** | Pega el enunciado completo y se resuelve solo |
| 📝 **Estilo cuaderno** | Cada iteración detallada con sustituciones |
| 📦 **Resultados enmarcados** | Valores importantes resaltados visualmente |
| 🏷️ **Badges de estado** | Verde (converge) / Amarillo (continuar) por iteración |
| 🌗 **Tema oscuro/claro** | Toggle con un clic |
| 📱 **Responsive** | Funciona en móvil, tablet y desktop |
| 📊 **Gráficas** | Convergencia del error con Chart.js |
| 📥 **Exportar** | Descarga el procedimiento como `.txt` |
| 📋 **Tabla resumen** | Al final de cada resolución |
| 🔢 **Normalización** | Acepta `sen`, `ln`, `e^x`, `√`, `π`, `x²` |

---

## 📦 Uso

1. Abre `index.html` en cualquier navegador moderno
2. **Opción A:** Pega el enunciado en la "Entrada Inteligente" y presiona **Analizar y Resolver**
3. **Opción B:** Selecciona la pestaña del método, ingresa los datos manualmente y presiona **Resolver**
4. Observa el desarrollo completo paso a paso

> **No requiere instalación, servidor ni dependencias locales** — funciona directamente en el navegador.

---

## 🛠️ Tecnologías

- **HTML5, CSS3, JavaScript Vanilla** — Sin frameworks, un solo archivo
- **[Chart.js](https://www.chartjs.org/)** — Gráficas de convergencia
- **[math.js](https://mathjs.org/)** — Evaluación segura de expresiones matemáticas
- **Google Fonts** — Space Grotesk + JetBrains Mono
- **Diseño Glassmorphism** — Estética moderna con backdrop-filter

---

## 📂 Estructura del Proyecto

```
MetResp/
├── index.html    ← Aplicación completa (un solo archivo)
├── README.md     ← Este archivo
└── LICENSE       ← Licencia MIT
```

---

## 📄 Licencia

Este proyecto está bajo la licencia [MIT](LICENSE).

---

<p align="center">
  Hecho con ❤️ por <strong>Fisbert</strong> — 2026
</p>
