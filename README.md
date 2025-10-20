# 📊 Presentación Focos Estratégicos UNIACC

Guía completa para modificar y personalizar la presentación Vue.js

## 📁 Estructura del Proyecto

```
presentacion-uniacc-vue/
├── src/
│   ├── components/
│   │   └── FocosUNIACCPresentation.vue  ← Archivo principal a modificar
│   ├── assets/
│   │   └── main.css
│   ├── App.vue
│   └── main.js
├── tailwind.config.js
├── package.json
└── README.md
```

## 🚀 Comandos Básicos

```bash
# Instalar dependencias (solo la primera vez)
npm install

# Iniciar servidor de desarrollo
npm run dev

# Compilar para producción
npm run build

# Vista previa del build
npm run preview
```

---

## ✏️ Cómo Modificar el Contenido

### 📍 Ubicación del Código

Todo el contenido editable está en: `src/components/FocosUNIACCPresentation.vue`

Busca la sección `<script setup>` y encontrarás el array `slides`:

```javascript
const slides = [
  { /* slide 1 */ },
  { /* slide 2 */ },
  // etc...
]
```

---

## 🎯 Modificar Slides Existentes

### 1️⃣ Cambiar Textos de una Slide

**Ejemplo: Modificar el título de Matrícula**

```javascript
{
  icon: Users,
  color: "bg-blue-600",
  title: "1. Matrícula / Admisión",  // ← Cambia aquí el título
  definition: "Tu nueva definición aquí...",  // ← Cambia la definición
  alcance: [
    "Primer punto del alcance",  // ← Modifica los puntos
    "Segundo punto",
    // Agrega o elimina puntos según necesites
  ],
  indicadores: [
    "Indicador 1",  // ← Modifica los indicadores
    "Indicador 2",
  ]
}
```

### 2️⃣ Agregar o Quitar Puntos de Alcance/Indicadores

**Para agregar un punto:**
```javascript
alcance: [
  "Punto existente 1",
  "Punto existente 2",
  "NUEVO PUNTO AQUÍ",  // ← Simplemente agrega una nueva línea
]
```

**Para eliminar un punto:**
```javascript
alcance: [
  "Punto 1",
  // "Punto 2",  ← Comenta o elimina la línea
  "Punto 3",
]
```

---

## ➕ Agregar una Nueva Slide

### Slide de Contenido Regular

Agrega un nuevo objeto al array `slides`:

```javascript
const slides = [
  // ... slides existentes ...
  
  // NUEVA SLIDE
  {
    icon: Users,  // Icono (Users, RefreshCw, TrendingDown, Heart, Award)
    color: "bg-blue-600",  // Color del fondo del icono
    title: "Título de tu Nueva Slide",
    definition: "Definición o descripción principal",
    alcance: [
      "Punto 1 del alcance",
      "Punto 2 del alcance",
      "Punto 3 del alcance",
    ],
    indicadores: [
      "Indicador 1",
      "Indicador 2",
      "Indicador 3",
    ]
  }
]
```

### Slide de Interrelación (tipo conexiones)

```javascript
{
  title: "Título de la Slide",
  isInterrelation: true,  // ← Marca como slide de interrelación
  connections: [
    {
      from: "Concepto Origen",
      to: "Concepto Destino",
      impact: "Descripción del impacto o relación"
    },
    // Agrega más conexiones según necesites
  ],
  note: "Nota final o conclusión"
}
```

---

## 🎨 Cambiar Colores

### Colores de Focos

Los colores se definen con clases de Tailwind CSS. Busca estas líneas:

```javascript
color: "bg-blue-600",  // Fondo azul
```

**Colores disponibles:**
- `bg-blue-600` - Azul (Matrícula)
- `bg-green-600` - Verde (Rematrícula)
- `bg-orange-600` - Naranja (Retención)
- `bg-purple-600` - Morado (Alumno en Centro)
- `bg-amber-500` - Ámbar/Amarillo (Acreditación)
- `bg-red-600` - Rojo
- `bg-pink-600` - Rosa
- `bg-indigo-600` - Índigo
- `bg-slate-600` - Gris

### Cambiar Color de Todo un Foco

Si quieres cambiar el color de "Matrícula" de azul a verde:

**1. En el array `slides`, cambia:**
```javascript
{
  icon: Users,
  color: "bg-green-600",  // ← Cambiado de blue a green
  title: "1. Matrícula / Admisión",
  // ...
}
```

**2. En la slide de flujo visual, busca y cambia todos los colores azules:**
```vue
<!-- Busca secciones como esta -->
<div class="bg-blue-50 border-3 border-blue-500...">
  <!-- Cambia a: -->
  <div class="bg-green-50 border-3 border-green-500...">
</div>

<div class="bg-blue-600...">
  <!-- Cambia a: -->
  <div class="bg-green-600...">
</div>

<p class="text-blue-900...">
  <!-- Cambia a: -->
  <p class="text-green-900...">
</p>
```

**Patrón de colores de Tailwind:**
- `bg-[color]-50` - Fondo muy claro
- `bg-[color]-100` - Fondo claro
- `bg-[color]-500` - Color medio (bordes)
- `bg-[color]-600` - Color principal
- `text-[color]-700` - Texto medio
- `text-[color]-900` - Texto oscuro
- `border-[color]-500` - Borde

---

## 🔄 Cambiar el Orden de las Slides

Simplemente reordena los objetos en el array:

```javascript
const slides = [
  { /* Portada */ },
  { /* Flujo Visual */ },
  { /* Acreditación */ },  // ← Puedes mover esta...
  { /* Matrícula */ },
  { /* Rematrícula */ },
  // ... aquí abajo, por ejemplo
]
```

---

## 🗑️ Eliminar una Slide

Simplemente comenta o elimina el objeto completo:

```javascript
const slides = [
  { /* Portada */ },
  { /* Flujo Visual */ },
  // {
  //   icon: Award,
  //   color: "bg-amber-500",
  //   title: "Meta Institucional: Acreditación 2026",
  //   // ... resto del código comentado
  // },
  { /* Siguiente slide */ },
]
```

---

## 📝 Modificar la Slide de Flujo Visual (Slide 2)

Esta es la slide más compleja. Busca la sección que dice:

```vue
<!-- NUEVA: Slide de Flujo Visual (segunda slide) -->
<div v-if="currentSlide.isFlujoVisual" class="space-y-4">
```

### Cambiar textos del Header de Acreditación:

```vue
<h2 class="text-2xl font-bold text-white">META: ACREDITACIÓN 2026</h2>
<!-- Cambia el año o el texto aquí -->

<p class="text-amber-100 text-sm">Todos los focos estratégicos tributan a este objetivo institucional</p>
<!-- Cambia el subtítulo aquí -->
```

### Modificar puntos de cada columna:

**Columna Matrícula:**
```vue
<div class="bg-white p-2 rounded border border-blue-300">
  <p class="text-xs font-bold text-blue-900">1. Prospecto</p>
  <p class="text-xs text-slate-600">Marketing/Difusión</p>
</div>
<!-- Duplica este bloque para agregar más pasos -->
```

**Columna Centro (El Alumno en el Centro):**
```vue
<div class="bg-white p-2 rounded-lg border-2 border-purple-300">
  <p class="text-xs font-bold text-purple-900">Escucha Activa</p>
  <p class="text-xs text-slate-600">Feedback estudiantil</p>
</div>
<!-- Duplica para agregar más elementos -->
```

**Columnas Rematrícula y Retención:**
Similar a Matrícula, busca los bloques con `✓` o `⚠` y modifica.

---

## 🎨 Personalización Avanzada

### Cambiar Íconos

Los íconos disponibles son de `lucide-vue-next`. Para usar otros:

1. Importa el ícono en la sección de imports:
```javascript
import { 
  ChevronLeft, 
  ChevronRight, 
  Users, 
  RefreshCw, 
  TrendingDown, 
  Heart, 
  Award,
  Star,  // ← Nuevo ícono
  Target,  // ← Otro nuevo
} from 'lucide-vue-next'
```

2. Úsalo en una slide:
```javascript
{
  icon: Star,  // ← Usa el nuevo ícono
  color: "bg-yellow-600",
  title: "Nueva Sección",
  // ...
}
```

**Íconos comunes disponibles:**
- `Users` - Personas
- `RefreshCw` - Renovación/Ciclo
- `TrendingDown` - Tendencia/Retención
- `Heart` - Corazón
- `Award` - Premio/Certificado
- `Target` - Objetivo
- `Star` - Estrella
- `CheckCircle` - Check
- `AlertCircle` - Alerta
- `BarChart` - Gráfico

Ver más íconos en: https://lucide.dev/icons/

### Cambiar Tamaños de Texto

```vue
<!-- Títulos -->
<h1 class="text-5xl...">  ← Extra grande
<h2 class="text-4xl...">  ← Grande
<h3 class="text-2xl...">  ← Mediano
<h4 class="text-xl...">   ← Normal grande
<p class="text-lg...">    ← Normal
<p class="text-sm...">    ← Pequeño
<p class="text-xs...">    ← Extra pequeño
```

---

## 🐛 Solución de Problemas

### Los cambios no se reflejan

1. Asegúrate de guardar el archivo (`Ctrl+S` o `Cmd+S`)
2. El servidor debería recargar automáticamente
3. Si no, detén (`Ctrl+C`) y reinicia: `npm run dev`
4. Limpia la caché del navegador (`Ctrl+Shift+R` o `Cmd+Shift+R`)

### Error de sintaxis

- Verifica que todas las comas estén en su lugar
- Asegúrate de cerrar todos los corchetes `[]` y llaves `{}`
- Revisa que todas las comillas estén cerradas `"texto"`

### Ícono no aparece

- Verifica que el ícono esté importado en la sección de imports
- El nombre debe ser exactamente igual (case-sensitive)

---

## 📦 Exportar para Producción

```bash
# Genera los archivos optimizados en la carpeta dist/
npm run build

# Los archivos en dist/ están listos para subir a un servidor
```

---

## 🎓 Ejemplos Prácticos

### Ejemplo 1: Cambiar el año de acreditación de 2026 a 2027

**En el array slides:**
```javascript
{
  icon: Award,
  color: "bg-amber-500",
  title: "Meta Institucional: Acreditación 2027",  // ← Cambiar aquí
  // ...
}
```

**En la portada:**
```vue
<p class="font-bold text-amber-900 text-lg">Meta: Acreditación 2027</p>
```

**En el flujo visual:**
```vue
<h2 class="text-2xl font-bold text-white">META: ACREDITACIÓN 2027</h2>
<p class="text-xl font-bold text-amber-600">2027</p>
```

### Ejemplo 2: Agregar un nuevo punto a Matrícula

```javascript
{
  icon: Users,
  color: "bg-blue-600",
  title: "1. Matrícula / Admisión",
  definition: "Captación y conversión efectiva de nuevos estudiantes que ingresan por primera vez a UNIACC",
  alcance: [
    "Atracción de prospectos (marketing y difusión)",
    "Proceso de postulación y evaluación",
    "Acompañamiento en admisión (info académica/financiera)",
    "Formalización de matrícula",
    "Onboarding e integración inicial",
    "Seguimiento durante el primer mes"  // ← NUEVO PUNTO
  ],
  indicadores: [
    "N° de postulantes",
    "Tasa de conversión",
    "Cumplimiento de metas por carrera"
  ]
}
```

### Ejemplo 3: Cambiar color de Rematrícula a azul

1. En el array:
```javascript
{
  icon: RefreshCw,
  color: "bg-blue-600",  // ← Cambiar de green a blue
  title: "2. Rematrícula Alumnos Antiguos",
  // ...
}
```

2. En la slide de flujo visual, busca todas las clases `green` y cámbiala a `blue`:
- `bg-green-50` → `bg-blue-50`
- `border-green-500` → `border-blue-500`
- `bg-green-600` → `bg-blue-600`
- `text-green-900` → `text-blue-900`
- etc.

---

## 📞 Ayuda Adicional

Si necesitas ayuda o encuentras algún problema:

1. Revisa la consola del navegador (F12) para ver errores
2. Verifica que todas las dependencias estén instaladas: `npm install`
3. Asegúrate de estar usando Node.js versión 18 o superior: `node --version`

---

## 🎉 ¡Listo!

Ahora tienes todo lo necesario para modificar y personalizar tu presentación. 

**Recuerda:**
- Siempre guarda los cambios
- Prueba cada modificación antes de hacer la siguiente
- Haz copias de seguridad antes de cambios grandes

¡Buena suerte con tu presentación! 🚀