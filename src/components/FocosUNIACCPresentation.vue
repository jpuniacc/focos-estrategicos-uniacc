<script setup>
import { ref, computed } from 'vue'
import { 
  ChevronLeft, 
  ChevronRight, 
  Users, 
  RefreshCw, 
  TrendingDown, 
  Heart, 
  Award 
} from 'lucide-vue-next'

const currentSlideIndex = ref(0)

const slides = [
  {
    
    title: "Focos Estratégicos Dirección de Transformación Digital e Innovación",
    subtitle: "Marco para evaluación de iniciativas institucionales",
    isTitle: true
  },
  {
    // NUEVA SLIDE: Flujo Visual Integrado
    isFlujoVisual: true
  },
  {
    icon: Award,
    color: "bg-amber-500",
    title: "Meta Institucional: Acreditación 2026",
    definition: "Objetivo estratégico que articula y da sentido a todos los esfuerzos institucionales, asegurando la calidad y reconocimiento de UNIACC",
    alcance: [
      "Alineación de todas las iniciativas institucionales",
      "Mejora continua de procesos académicos y administrativos",
      "Cumplimiento de estándares de calidad establecidos por CNA",
      "Fortalecimiento de la gestión institucional",
      "Evidencia documentada de resultados y mejoras",
      "Participación activa de toda la comunidad universitaria"
    ],
    indicadores: [
      "Avance en criterios de acreditación",
      "Cumplimiento de compromisos de mejora",
      "Indicadores de calidad por dimensión",
      "Satisfacción de la comunidad universitaria"
    ],
    isAcreditacion: true
  },
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
      "Onboarding e integración inicial"
    ],
    indicadores: [
      "N° de postulantes",
      "Tasa de conversión",
      "Cumplimiento de metas por carrera"
    ]
  },
  {
    icon: RefreshCw,
    color: "bg-green-600",
    title: "2. Rematrícula Alumnos Antiguos",
    definition: "Retención y continuidad académica de estudiantes que renuevan su compromiso cada período",
    alcance: [
      "Seguimiento proactivo pre-rematrícula",
      "Gestión administrativa y financiera",
      "Resolución de barreras (deudas, documentación)",
      "Comunicación oportuna de plazos",
      "Atención personalizada a casos especiales"
    ],
    indicadores: [
      "Tasa de rematrícula por cohorte",
      "% renovación oportuna",
      "Identificación temprana de riesgo"
    ]
  },
  {
    icon: TrendingDown,
    color: "bg-orange-600",
    title: "3. Disminuir Deserción",
    definition: "Prevención del abandono mediante identificación temprana de riesgos y acciones de retención",
    alcance: [
      "Detección de señales tempranas",
      "Programas de apoyo académico (tutorías, nivelación)",
      "Apoyo socioeconómico y ayudas estudiantiles",
      "Intervenciones psicoeducativas",
      "Seguimiento de bajo rendimiento y ausentismo",
      "Análisis de causas y mejora continua"
    ],
    indicadores: [
      "Tasa de deserción (semestral/anual)",
      "Tasa de retención 1er año",
      "Efectividad de intervenciones"
    ]
  },
  {
    icon: Heart,
    color: "bg-purple-600",
    title: "4. El Alumno en el Centro",
    definition: "Enfoque que prioriza la experiencia, necesidades y desarrollo integral del estudiante en todos los procesos",
    alcance: [
      "Experiencias académicas/administrativas centradas en el estudiante",
      "Canales de comunicación accesibles y empáticos",
      "Escucha activa y consideración de feedback",
      "Servicios de apoyo integral",
      "Personalización según necesidades",
      "Cultura orientada al éxito estudiantil"
    ],
    indicadores: [
      "Índice de satisfacción",
      "Net Promoter Score (NPS)",
      "Evaluación de servicios"
    ]
  },
  {
    title: "Interrelación de Focos",
    isInterrelation: true,
    connections: [
      {
        from: "Acreditación 2026",
        to: "Todos los focos",
        impact: "Es el objetivo superior que da sentido a todas las iniciativas"
      },
      {
        from: "Admisión",
        to: "Rematrícula y Deserción",
        impact: "Una buena experiencia inicial impacta positivamente"
      },
      {
        from: "Alumno en el Centro",
        to: "Todos los focos operacionales",
        impact: "Fortalece y potencia los tres focos operacionales"
      },
      {
        from: "Disminución Deserción",
        to: "Rematrícula",
        impact: "Mejora naturalmente las tasas de continuidad"
      }
    ],
    note: "Cada iniciativa debe explicitar a qué foco(s) tributa, cómo contribuye a Acreditación 2026 y cómo medirá su contribución"
  }
]

const currentSlide = computed(() => slides[currentSlideIndex.value])

const nextSlide = () => {
  currentSlideIndex.value = (currentSlideIndex.value + 1) % slides.length
}

const prevSlide = () => {
  currentSlideIndex.value = (currentSlideIndex.value - 1 + slides.length) % slides.length
}
</script>

<template>
  <div class="w-full min-h-screen bg-gradient-to-br from-slate-900 to-slate-800 flex flex-col">
    <div class="flex-1 flex items-center justify-center p-4 sm:p-6 lg:p-8">
      <div class="w-full max-w-5xl bg-white rounded-lg shadow-2xl p-4 sm:p-6 lg:p-12">
        
        <!-- Slide de Portada -->
        <div v-if="currentSlide.isTitle" class="text-center space-y-6">
          <img src="/logo_uniacc.svg" alt="UNIACC" class="w-20 h-20 sm:w-32 sm:h-32 lg:w-40 lg:h-40 mx-auto mb-4" />
          <h1 class="text-2xl sm:text-3xl lg:text-5xl font-bold text-slate-800 mb-4">
            {{ currentSlide.title }}
          </h1>
          <p class="text-lg sm:text-xl lg:text-2xl text-slate-600">
            {{ currentSlide.subtitle }}
          </p>
          <div class="mt-8 sm:mt-12 grid grid-cols-1 sm:grid-cols-3 gap-4 sm:gap-6">
            <div class="col-span-1 sm:col-span-3 bg-amber-50 p-4 sm:p-6 rounded-lg border-2 border-amber-400">
              <Award class="w-12 h-12 text-amber-600 mx-auto mb-3" />
              <p class="font-bold text-amber-900 text-lg">Meta: Acreditación 2026</p>
              <p class="text-sm text-amber-700">Objetivo institucional prioritario</p>
            </div>
            <div class="bg-blue-50 p-4 sm:p-6 rounded-lg">
              <Users class="w-12 h-12 text-blue-600 mx-auto mb-3" />
              <p class="font-semibold text-blue-900">Matrícula</p>
            </div>
            <div class="bg-green-50 p-4 sm:p-6 rounded-lg">
              <RefreshCw class="w-12 h-12 text-green-600 mx-auto mb-3" />
              <p class="font-semibold text-green-900">Rematrícula</p>
            </div>
            <div class="bg-orange-50 p-4 sm:p-6 rounded-lg">
              <TrendingDown class="w-12 h-12 text-orange-600 mx-auto mb-3" />
              <p class="font-semibold text-orange-900">Disminuir Deserción</p>
            </div>
            <div class="col-span-1 sm:col-span-3 bg-purple-50 p-4 sm:p-6 rounded-lg">
              <Heart class="w-12 h-12 text-purple-600 mx-auto mb-3" />
              <p class="font-semibold text-purple-900">El Alumno en el Centro</p>
              <p class="text-sm text-purple-700">Núcleo transversal</p>
            </div>
          </div>
        </div>

        <!-- NUEVA: Slide de Flujo Visual (segunda slide) -->
        <div v-if="currentSlide.isFlujoVisual" class="space-y-4">
          <!-- Header Acreditación -->
          <div class="bg-gradient-to-r from-amber-500 to-yellow-500 rounded-xl p-4 mb-4">
            <div class="flex items-center justify-between">
              <div class="flex items-center gap-3">
                <div class="bg-white p-2 rounded-lg">
                  <Award class="w-8 h-8 text-amber-600" />
                </div>
                <div>
                  <h2 class="text-2xl font-bold text-white">META: ACREDITACIÓN 2026</h2>
                  <p class="text-amber-100 text-sm">Todos los focos estratégicos tributan a este objetivo institucional</p>
                </div>
              </div>
              <div class="bg-white px-4 py-2 rounded-lg">
                <p class="text-xl font-bold text-amber-600">2026</p>
              </div>
            </div>
          </div>

          <h3 class="text-lg sm:text-xl lg:text-2xl font-bold text-slate-800 text-center mb-4">Focos Estratégicos - Ciclo de Vida del Estudiante</h3>

          <!-- Grid responsive -->
          <div class="grid grid-cols-1 lg:grid-cols-12 gap-3">
            <!-- Columna 1: Matrícula -->
            <div class="lg:col-span-3">
              <div class="bg-blue-50 border-3 border-blue-500 rounded-xl p-3 h-full">
                <div class="flex items-center gap-2 mb-3">
                  <div class="bg-blue-600 p-2 rounded-lg">
                    <Users class="w-6 h-6 text-white" />
                  </div>
                  <div>
                    <h4 class="text-lg font-bold text-blue-900">MATRÍCULA</h4>
                    <p class="text-xs text-blue-700">Admisión</p>
                  </div>
                </div>
                <div class="space-y-2">
                  <div class="bg-white p-2 rounded border border-blue-300">
                    <p class="text-xs font-bold text-blue-900">1. Prospecto</p>
                    <p class="text-xs text-slate-600">Marketing/Difusión</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-blue-300">
                    <p class="text-xs font-bold text-blue-900">2. Postulación</p>
                    <p class="text-xs text-slate-600">Evaluación</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-blue-300">
                    <p class="text-xs font-bold text-blue-900">3. Admisión</p>
                    <p class="text-xs text-slate-600">Acompañamiento</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-blue-300">
                    <p class="text-xs font-bold text-blue-900">4. Matrícula</p>
                    <p class="text-xs text-slate-600">Onboarding</p>
                  </div>
                </div>
                <div class="mt-3 bg-blue-100 p-2 rounded">
                  <p class="text-xs font-semibold text-blue-800">📊 Indicadores</p>
                  <p class="text-xs text-blue-700">N° postulantes, Tasa conversión</p>
                </div>
              </div>
            </div>

            <!-- Columna 2: Alumno en el Centro -->
            <div class="lg:col-span-6 flex flex-col justify-center mt-3 lg:mt-0">
              <div class="bg-purple-100 border-3 border-purple-600 rounded-xl p-4 mb-3 relative">
                <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-purple-600 text-white px-3 py-1 rounded-full text-xs font-bold">
                  ⭐ NÚCLEO ESTRATÉGICO
                </div>
                <div class="flex flex-col items-center text-center mt-2">
                  <div class="bg-purple-600 p-3 rounded-full mb-2">
                    <Heart class="w-8 h-8 text-white" />
                  </div>
                  <h4 class="text-xl font-bold text-purple-900 mb-1">EL ALUMNO EN EL CENTRO</h4>
                  <p class="text-purple-700 text-sm mb-3">Experiencia integral y servicios personalizados</p>
                  
                  <div class="grid grid-cols-2 gap-2 w-full">
                    <div class="bg-white p-2 rounded-lg border-2 border-purple-300">
                      <p class="text-xs font-bold text-purple-900">Escucha Activa</p>
                      <p class="text-xs text-slate-600">Feedback estudiantil</p>
                    </div>
                    <div class="bg-white p-2 rounded-lg border-2 border-purple-300">
                      <p class="text-xs font-bold text-purple-900">Apoyo Integral</p>
                      <p class="text-xs text-slate-600">Académico/Emocional</p>
                    </div>
                    <div class="bg-white p-2 rounded-lg border-2 border-purple-300">
                      <p class="text-xs font-bold text-purple-900">Comunicación</p>
                      <p class="text-xs text-slate-600">Canales accesibles</p>
                    </div>
                    <div class="bg-white p-2 rounded-lg border-2 border-purple-300">
                      <p class="text-xs font-bold text-purple-900">Personalización</p>
                      <p class="text-xs text-slate-600">Según necesidades</p>
                    </div>
                  </div>

                  <div class="mt-2 bg-purple-200 p-2 rounded-lg w-full">
                    <p class="text-xs font-semibold text-purple-900">📊 Indicadores: NPS, Satisfacción, Evaluación servicios</p>
                  </div>
                </div>
              </div>

              <div class="flex items-center justify-center gap-4 text-sm">
                <div class="flex items-center gap-1">
                  <div class="w-12 h-0.5 bg-green-400"></div>
                  <span class="text-green-600 font-bold">←→</span>
                  <div class="w-12 h-0.5 bg-green-400"></div>
                </div>
                <div class="bg-slate-200 px-3 py-1 rounded-lg">
                  <p class="text-xs font-bold text-slate-700">Ciclo Continuo del Estudiante</p>
                </div>
                <div class="flex items-center gap-1">
                  <div class="w-12 h-0.5 bg-orange-400"></div>
                  <span class="text-orange-600 font-bold">←→</span>
                  <div class="w-12 h-0.5 bg-orange-400"></div>
                </div>
              </div>
            </div>

            <!-- Columna 3: Rematrícula y Retención -->
            <div class="lg:col-span-3 flex flex-col gap-3 mt-3 lg:mt-0">
              <!-- Rematrícula -->
              <div class="bg-green-50 border-3 border-green-500 rounded-xl p-3">
                <div class="flex items-center gap-2 mb-2">
                  <div class="bg-green-600 p-2 rounded-lg">
                    <RefreshCw class="w-5 h-5 text-white" />
                  </div>
                  <div>
                    <h4 class="text-lg font-bold text-green-900">REMATRÍCULA</h4>
                    <p class="text-xs text-green-700">Continuidad</p>
                  </div>
                </div>
                <div class="space-y-1">
                  <div class="bg-white p-2 rounded border border-green-300">
                    <p class="text-xs font-bold text-green-900">✓ Seguimiento proactivo</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-green-300">
                    <p class="text-xs font-bold text-green-900">✓ Gestión administrativa</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-green-300">
                    <p class="text-xs font-bold text-green-900">✓ Resolución barreras</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-green-300">
                    <p class="text-xs font-bold text-green-900">✓ Renovación oportuna</p>
                  </div>
                </div>
                <div class="mt-2 bg-green-100 p-2 rounded">
                  <p class="text-xs font-semibold text-green-800">📊 Indicadores</p>
                  <p class="text-xs text-green-700">Tasa rematrícula, Renovación</p>
                </div>
              </div>

              <!-- Retención -->
              <div class="bg-orange-50 border-3 border-orange-500 rounded-xl p-3">
                <div class="flex items-center gap-2 mb-2">
                  <div class="bg-orange-600 p-2 rounded-lg">
                    <TrendingDown class="w-5 h-5 text-white" />
                  </div>
                  <div>
                    <h4 class="text-lg font-bold text-orange-900">RETENCIÓN</h4>
                    <p class="text-xs text-orange-700">Prevención</p>
                  </div>
                </div>
                <div class="space-y-1">
                  <div class="bg-white p-2 rounded border border-orange-300">
                    <p class="text-xs font-bold text-orange-900">⚠ Detección temprana</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-orange-300">
                    <p class="text-xs font-bold text-orange-900">⚠ Apoyo académico</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-orange-300">
                    <p class="text-xs font-bold text-orange-900">⚠ Apoyo socioeconómico</p>
                  </div>
                  <div class="bg-white p-2 rounded border border-orange-300">
                    <p class="text-xs font-bold text-orange-900">⚠ Intervención oportuna</p>
                  </div>
                </div>
                <div class="mt-2 bg-orange-100 p-2 rounded">
                  <p class="text-xs font-semibold text-orange-800">📊 Indicadores</p>
                  <p class="text-xs text-orange-700">Tasa deserción, Retención 1er año</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Footer -->
          <div class="mt-3 bg-gradient-to-r from-slate-700 to-slate-600 rounded-xl p-3">
            <p class="text-white text-center text-xs font-semibold">
              💡 Cada iniciativa debe identificar: <span class="text-yellow-300">¿A qué foco(s) tributa?</span> • <span class="text-yellow-300">¿Qué indicador impacta?</span> • <span class="text-yellow-300">¿Cómo contribuye a Acreditación 2026?</span>
            </p>
          </div>
        </div>

        <!-- Slide de Interrelación -->
        <div v-if="currentSlide.isInterrelation" class="space-y-6">
          <h2 class="text-2xl sm:text-3xl lg:text-4xl font-bold text-slate-800 mb-8">
            {{ currentSlide.title }}
          </h2>
          
          <div class="space-y-4 mb-8">
            <div 
              v-for="(conn, idx) in currentSlide.connections" 
              :key="idx"
              :class="[
                'p-6 rounded-lg border-l-4',
                idx === 0 ? 'bg-amber-50 border-amber-500' : 'bg-slate-50 border-blue-500'
              ]"
            >
              <div class="flex items-center gap-3 mb-2">
                <span :class="['font-bold', idx === 0 ? 'text-amber-600' : 'text-blue-600']">
                  {{ conn.from }}
                </span>
                <span class="text-slate-400">→</span>
                <span class="font-bold text-slate-700">{{ conn.to }}</span>
              </div>
              <p class="text-slate-600">{{ conn.impact }}</p>
            </div>
          </div>

          <div class="bg-purple-50 border-2 border-purple-200 rounded-lg p-6">
            <p class="text-lg text-purple-900 font-semibold">
              📌 {{ currentSlide.note }}
            </p>
          </div>
        </div>

        <!-- Slides de Focos -->
        <div v-if="!currentSlide.isTitle && !currentSlide.isInterrelation && !currentSlide.isFlujoVisual" class="space-y-6">
          <div class="flex items-center gap-4 mb-6">
            <div :class="[currentSlide.color, 'p-3 rounded-lg']">
              <component :is="currentSlide.icon" class="w-10 h-10 text-white" />
            </div>
            <h2 class="text-2xl sm:text-3xl lg:text-4xl font-bold text-slate-800">
              {{ currentSlide.title }}
            </h2>
          </div>

          <div v-if="currentSlide.isAcreditacion" class="bg-amber-100 border-l-4 border-amber-500 p-4 mb-4 rounded">
            <p class="text-amber-900 font-semibold">
              ⭐ Este es el objetivo superior que da sentido y dirección a todos los demás focos
            </p>
          </div>

          <div class="bg-slate-50 p-6 rounded-lg mb-6">
            <h3 class="text-sm font-semibold text-slate-500 uppercase mb-2">
              Definición
            </h3>
            <p class="text-lg text-slate-700">
              {{ currentSlide.definition }}
            </p>
          </div>

          <div class="grid grid-cols-2 gap-6">
            <div>
              <h3 class="text-sm font-semibold text-slate-500 uppercase mb-3">
                Alcance
              </h3>
              <ul class="space-y-2">
                <li v-for="(item, idx) in currentSlide.alcance" :key="idx" class="flex items-start gap-2">
                  <span class="text-blue-500 mt-1">•</span>
                  <span class="text-slate-700">{{ item }}</span>
                </li>
              </ul>
            </div>

            <div>
              <h3 class="text-sm font-semibold text-slate-500 uppercase mb-3">
                Indicadores Clave
              </h3>
              <ul class="space-y-2">
                <li v-for="(item, idx) in currentSlide.indicadores" :key="idx" class="flex items-start gap-2">
                  <span class="text-green-500 mt-1">✓</span>
                  <span class="text-slate-700">{{ item }}</span>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Navegación -->
    <div class="bg-slate-800 p-2 sm:p-4 flex items-center justify-between">
      <button
        @click="prevSlide"
        class="flex items-center gap-1 sm:gap-2 px-2 sm:px-4 py-2 bg-slate-700 hover:bg-slate-600 text-white rounded-lg transition text-sm sm:text-base"
      >
        <ChevronLeft class="w-4 h-4 sm:w-5 sm:h-5" />
        <span class="hidden sm:inline">Anterior</span>
      </button>

      <div class="flex gap-1 sm:gap-2">
        <button
          v-for="(slide, idx) in slides"
          :key="idx"
          @click="currentSlideIndex = idx"
          :class="[
            'w-2 h-2 sm:w-3 sm:h-3 rounded-full transition',
            idx === currentSlideIndex ? 'bg-white' : 'bg-slate-600'
          ]"
        />
      </div>

      <button
        @click="nextSlide"
        class="flex items-center gap-1 sm:gap-2 px-2 sm:px-4 py-2 bg-slate-700 hover:bg-slate-600 text-white rounded-lg transition text-sm sm:text-base"
      >
        <span class="hidden sm:inline">Siguiente</span>
        <ChevronRight class="w-4 h-4 sm:w-5 sm:h-5" />
      </button>
    </div>
  </div>
</template>