<script setup>
import { ref } from 'vue'
// ⭐ AGREGA ESTAS IMPORTACIONES DE LUCIDE
import { GraduationCap, Code, Briefcase, BookOpen } from 'lucide-vue-next'

const fechaColor = ref([])
const hoveredItem = ref(null)

const fechaColor_value = [
  { color: '#1a1c1e' },
  { color: '#d4cdc3' },
  { color: '#a09282' },
  { color: '#3a3e3c' },
  { color: '#e4d9cb' },
]

const education = [
  {
    id: 1,
    fecha: '2024',
    title: 'Tecnicatura Universitaria en Programación',
    institution: 'Universidad Tecnológica Nacional',
    descripcion:
      'Incumbencias Profesionales: Operación y programación de computadoras, desarrollo de programas en distintos lenguajes, análisis y control de sistemas informáticos.',
    enlace: 'http://www.youtube.com/',
    iconComponent: GraduationCap, // ⭐ CAMBIA: usa el componente en lugar de emoji
    colorClass: 'color-burgundy',
    badgeClass: 'badge-burgundy',
    iconClass: 'icon-burgundy',
  },
  {
    id: 2,
    fecha: '2023',
    title: 'Desarrollador Full Stack',
    institution: 'KV2 Tech',
    descripcion:
      'Trabajé en KV2 Tech donde diseñé y desarrollé aplicaciones web complejas utilizando tecnologías como Node.js, React y MongoDB.',
    enlace: 'http://www.direccion.com',
    iconComponent: Code, // ⭐ CAMBIA: componente de código
    colorClass: 'color-gold',
    badgeClass: 'badge-gold',
    iconClass: 'icon-gold',
  },
  {
    id: 3,
    fecha: '2022',
    title: 'Internship en Desarrollo Web',
    institution: 'ABC Solutions',
    descripcion:
      'Realicé una pasantía en ABC Solutions, contribuyendo en la creación de interfaces de usuario y optimización de sitios web.',
    enlace: 'http://www.direccion.com',
    iconComponent: Briefcase, // ⭐ CAMBIA: componente de maletín
    colorClass: 'color-terracotta',
    badgeClass: 'badge-terracotta',
    iconClass: 'icon-terracotta',
  },
  {
    id: 4,
    fecha: '2020',
    title: 'Curso de Introducción a la Programación',
    institution: 'Plataforma Online',
    descripcion:
      'Completé un curso en línea sobre fundamentos de programación, donde aprendí lenguajes como Python y Java.',
    enlace: 'http://www.direccion.com',
    iconComponent: BookOpen, // ⭐ CAMBIA: componente de libro
    colorClass: 'color-sage',
    badgeClass: 'badge-sage',
    iconClass: 'icon-sage',
  },
]
</script>

<template>
  <div id="educacion" class="education-section">
    ...
    <div class="container">
      <!-- Header -->
      <div class="header-section">
        <div class="title-wrapper">
          <h2 class="main-title">
            Educación - Cursos
            <div class="title-underline"></div>
          </h2>
        </div>
        <p class="subtitle">Mi trayectoria académica y profesional en el desarrollo de software</p>
      </div>

      <!-- Timeline -->
      <div class="timeline-wrapper">
        <div class="timeline-line"></div>

        <!-- Recorrer items con v-for -->
        <div
          v-for="(item, index) in education"
          :key="item.id"
          :class="['timeline-item', index % 2 === 0 ? 'left' : 'right']"
          @mouseenter="hoveredItem = item.id"
          @mouseleave="hoveredItem = null"
        >
          <!-- Para items izquierdos -->
          <template v-if="index % 2 === 0">
            <div
              class="timeline-content"
              :class="{ hovered: hoveredItem === item.id, [item.colorClass]: true }"
            >
              <div :class="['year-badge', item.badgeClass]">{{ item.fecha }}</div>
              <!-- DESPUÉS (con Lucide) -->
              <div :class="['icon-wrapper', item.iconClass]">
                <component
                  :is="item.iconComponent"
                  :size="28"
                  :stroke-width="2"
                  class="icon-lucide"
                />
              </div>
              <h3 class="item-title">{{ item.title }}</h3>
              <p class="item-institution">{{ item.institution }}</p>
              <p class="item-description">{{ item.descripcion }}</p>
              <a :href="item.enlace" class="learn-more" target="_blank">Saber más →</a>
              <div class="arrow-decorator arrow-right"></div>
            </div>
            <div class="timeline-dot"></div>
            <div class="timeline-spacer"></div>
          </template>

          <!-- Para items derechos -->
          <template v-else>
            <div class="timeline-spacer"></div>
            <div class="timeline-dot"></div>
            <div
              class="timeline-content"
              :class="{ hovered: hoveredItem === item.id, [item.colorClass]: true }"
            >
              <div :class="['year-badge', item.badgeClass]">{{ item.fecha }}</div>
              <div :class="['icon-wrapper', item.iconClass]">
                <span class="icon">{{ item.icon }}</span>
              </div>
              <h3 class="item-title">{{ item.title }}</h3>
              <p class="item-institution">{{ item.institution }}</p>
              <p class="item-description">{{ item.descripcion }}</p>
              <a :href="item.enlace" class="learn-more" target="_blank">Saber más →</a>
              <div class="arrow-decorator arrow-left"></div>
            </div>
          </template>
        </div>
      </div>

      <!-- Footer decorativo -->
      <div class="footer-decoration">
        <div class="pulse-dot"></div>
        <span>En constante aprendizaje</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Estilos generales */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap');
/* Reseteo de estilos básicos para todos los elementos y pseudo-elementos */
*,
*::before,
*::after {
  margin: 0; /* Elimina el margen predeterminado */
  padding: 0; /* Elimina el padding predeterminado */
  box-sizing: border-box; /* Incluye el padding y el borde en el tamaño total del elemento */
}

/* Estilo para el cuerpo de la página */
body {
  --color: rgba(30, 30, 30); /* Variable para el color de texto */
  --bgColor: rgba(245, 245, 245); /* Variable para el color de fondo */
  min-height: 100vh; /* Asegura que el cuerpo ocupe al menos el 100% de la altura de la ventana */
  display: grid; /* Utiliza el modelo de caja de cuadrícula */
  align-content: center; /* Centra verticalmente el contenido dentro de la cuadrícula */
  gap: 2rem; /* Espaciado entre los elementos de la cuadrícula */
  padding: 2rem; /* Espaciado interno alrededor del cuerpo */
  font-family: 'Poppins', sans-serif; /* Fuente para todo el texto en la página */
  color: var(--color); /* Aplica el color de texto definido en la variable */
  background: var(--bgColor); /* Aplica el color de fondo definido en la variable */
}

/* Estilos para la lista */
ul {
  margin-top: 2rem;
  --col-gap: 2rem; /* Espacio entre las columnas de la cuadrícula */
  --row-gap: 2rem; /* Espacio entre las filas de la cuadrícula */
  --line-w: 0.25rem; /* Ancho de la línea que conecta los elementos de la lista */
  display: grid; /* Usa un layout de cuadrícula */
  grid-template-columns: var(--line-w) 1fr; /* Define las columnas de la cuadrícula: la primera es la línea y la segunda es el contenido */
  grid-auto-columns: max-content; /* Las columnas se ajustan automáticamente al contenido */
  column-gap: var(--col-gap); /* Espacio entre las columnas */
  list-style: none; /* Elimina las viñetas predeterminadas de la lista */
  width: min(
    60rem,
    90%
  ); /* Limita el ancho de la lista al mínimo entre 60rem y el 90% del ancho de la ventana */
  margin-inline: auto; /* Centra la lista horizontalmente */
}

/* Estilo para la línea vertical que conecta los elementos de la lista */
ul::before {
  content: ''; /* Elemento vacío para crear la línea */
  grid-column: 1; /* Coloca la línea en la primera columna de la cuadrícula */
  grid-row: 1 / span 20; /* La línea se extiende sobre varias filas */
  background: rgb(225, 225, 225); /* Color de la línea */
  border-radius: calc(var(--line-w) / 2); /* Bordes redondeados para la línea */
}

/* Estilo para los elementos de la lista que no son el último */
ul li:not(:last-child) {
  margin-bottom: var(--row-gap); /* Espacio entre los elementos de la lista */
}

/* Estilo para cada ítem de la lista */
ul li {
  grid-column: 2; /* Coloca el contenido en la segunda columna de la cuadrícula */
  --inlineP: 1.5rem; /* Espacio interno horizontal dentro de cada ítem */
  margin-inline: var(--inlineP); /* Margen horizontal para los ítems */
  grid-row: span 2; /* Cada ítem ocupa dos filas en la cuadrícula */
  display: grid; /* Usa un layout de cuadrícula dentro de cada ítem */
  grid-template-rows: min-content min-content min-content; /* Define tres filas de altura mínima */
}

/* Estilo para la fecha dentro de cada ítem */
ul li .fecha {
  --dateH: 3rem; /* Altura de la sección de la fecha */
  height: var(--dateH); /* Aplica la altura definida */
  margin-inline: calc(
    var(--inlineP) * -1
  ); /* Ajusta el margen horizontal para que la fecha sobresalga */
  text-align: center; /* Centra el texto dentro de la fecha */
  background-color: var(--fecha-color); /* Color de fondo, usando una variable personalizada */
  color: white; /* Color del texto en la fecha */
  font-size: 1.25rem; /* Tamaño del texto */
  font-weight: 700; /* Hace el texto en negrita */
  display: grid; /* Usa un layout de cuadrícula */
  place-content: center; /* Centra el contenido de la fecha */
  position: relative; /* Posiciona la fecha relativa a su contenedor */
  border-radius: calc(var(--dateH) / 2) 0 0 calc(var(--dateH) / 2); /* Bordes redondeados para la fecha */
}

/* Estilo para la parte inferior de la fecha, que parece un triángulo */
ul li .fecha::before {
  content: ''; /* Elemento vacío para crear el triángulo */
  width: var(--inlineP); /* Ancho igual al espacio interno definido */
  aspect-ratio: 1; /* Mantiene una relación de aspecto 1:1 para crear un cuadrado */
  background: var(--fecha-color); /* Usa el color de fondo de la fecha */
  background-image: linear-gradient(
    rgba(0, 0, 0, 0.2) 100%,
    transparent
  ); /* Aplica un degradado sutil para dar un efecto de sombra */
  position: absolute; /* Posiciona el triángulo respecto al contenedor de la fecha */
  top: 100%; /* Coloca el triángulo justo debajo de la fecha */
  clip-path: polygon(
    0 0,
    100% 0,
    0 100%
  ); /* Recorta el cuadrado para convertirlo en un triángulo */
  right: 0; /* Alinea el triángulo a la derecha de la fecha */
}

/* Estilo para el círculo que conecta la fecha con la línea */
ul li .fecha::after {
  content: ''; /* Elemento vacío para crear el círculo */
  position: absolute; /* Posiciona el círculo respecto al contenedor de la fecha */
  width: 1rem; /* Ancho del círculo */
  aspect-ratio: 1; /* Mantiene una relación de aspecto 1:1 para crear un círculo */
  background: var(--bgColor); /* Color de fondo, utilizando la variable definida */
  border: 0.3rem solid var(--fecha-color); /* Borde del círculo, con el color de la fecha */
  border-radius: 50%; /* Hace que el elemento sea un círculo perfecto */
  top: 50%; /* Centra verticalmente el círculo dentro del contenedor de la fecha */
  transform: translate(50%, -50%); /* Ajusta la posición del círculo para alinearlo correctamente */
  right: calc(
    100% + var(--col-gap) + var(--line-w) / 2
  ); /* Coloca el círculo a la izquierda de la línea */
}

/* Estilos para el título y la descripción dentro de cada ítem */
ul li .title,
ul li .descripcion {
  background: var(--bgColor); /* Fondo del título y la descripción, usando la variable definida */
  position: relative; /* Posiciona los elementos relativos a su contenedor */
  padding-inline: 1.5rem; /* Espaciado interno horizontal */
}

ul li .title {
  overflow: hidden; /* Oculta cualquier contenido que se desborde */
  padding-block-start: 1.5rem; /* Espaciado interno superior */
  padding-block-end: 1rem; /* Espaciado interno inferior */
  font-weight: 500; /* Hace el texto del título un poco más grueso */
}

ul li .descripcion {
  padding-block-end: 1.5rem; /* Espaciado interno inferior */
  font-weight: 300; /* Hace el texto de la descripción más delgado */
}

/* Estilos para las sombras debajo del título y la descripción */
ul li .title::before,
ul li .descripcion::before {
  content: ''; /* Elemento vacío para crear la sombra */
  position: absolute; /* Posiciona la sombra respecto al contenedor del título o descripción */
  width: 90%; /* Ancho de la sombra */
  height: 0.5rem; /* Altura de la sombra */
  background: rgba(0, 0, 0, 0.5); /* Color de fondo oscuro para simular una sombra */
  left: 50%; /* Centra la sombra horizontalmente */
  border-radius: 50%; /* Bordes redondeados para la sombra */
  filter: blur(4px); /* Aplica un desenfoque para hacer la sombra más suave */
  transform: translate(-50%, 50%); /* Ajusta la posición para centrar la sombra */
}

ul li .title::before {
  bottom: calc(100% + 0.125rem); /* Coloca la sombra debajo del título */
}

ul li .descripcion::before {
  z-index: -1; /* Coloca la sombra detrás del contenido */
  bottom: 0.25rem; /* Coloca la sombra justo*/
}

/* Media query para pantallas anchas (40rem o más) */
@media (min-width: 40rem) {
  ul {
    grid-template-columns: 1fr var(--line-w) 1fr; /* Ajusta la cuadrícula para tener tres columnas */
  }
  ul::before {
    grid-column: 2; /* Mueve la línea vertical a la segunda columna de la cuadrícula */
  }
  ul li:nth-child(odd) {
    grid-column: 1; /* Coloca los ítems impares en la primera columna */
  }
  ul li:nth-child(even) {
    grid-column: 3; /* Coloca los ítems pares en la tercera columna */
  }

  /* Ajuste para que el segundo ítem abarque dos filas */
  ul li:nth-child(2) {
    grid-row: 2/4; /* El segundo ítem ocupará desde la segunda hasta la cuarta fila */
  }

  /* Ajustes específicos para los ítems impares */
  ul li:nth-child(odd) .fecha::before {
    clip-path: polygon(0 0, 100% 0, 100% 100%); /* Invierte el triángulo en los ítems impares */
    left: 0; /* Alinea el triángulo a la izquierda */
  }

  ul li:nth-child(odd) .fecha::after {
    transform: translate(-50%, -50%); /* Ajusta la posición del círculo en los ítems impares */
    left: calc(
      100% + var(--col-gap) + var(--line-w) / 2
    ); /* Coloca el círculo a la derecha de la línea */
  }

  ul li:nth-child(odd) .fecha {
    border-radius: 0 calc(var(--dateH) / 2) calc(var(--dateH) / 2) 0; /* Ajusta los bordes redondeados para los ítems impares */
  }
}

/* Estilo para los créditos */
.credits {
  margin-top: 1rem; /* Espaciado superior para los créditos */
  text-align: right; /* Alinea el texto de los créditos a la derecha */
}
.credits a {
  color: var(--color); /* Aplica el color de texto definido en la variable */
}
/* ========================================
  ESTILOS PARA SECCIÓN DE EDUCACIÓN
   ======================================== */

.education-section {
  min-height: 100vh;
  background-color: #f5f1ed;
  padding: 4rem 1rem;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

/* Header */
.header-section {
  text-align: center;
  margin-bottom: 5rem;
}

.title-wrapper {
  display: inline-block;
}

.main-title {
  font-size: 3rem;
  font-weight: bold;
  color: #6b4654;
  margin-bottom: 1rem;
  position: relative;
}

.title-underline {
  position: absolute;
  bottom: -0.5rem;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(to right, #c9756f, #d4af87, #747f6e);
  border-radius: 9999px;
}

.subtitle {
  color: #8b8680;
  margin-top: 1.5rem;
  font-size: 1.125rem;
  max-width: 42rem;
  margin-left: auto;
  margin-right: auto;
}

/* Timeline */
.timeline-wrapper {
  position: relative;
}

.timeline-line {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 100%;
  background: linear-gradient(to bottom, #6b4654, #c9756f, #747f6e);
  border-radius: 9999px;
}

/* Timeline Items */
.timeline-item {
  position: relative;
  display: flex;
  align-items: center;
  margin-bottom: 3rem;
}

.timeline-item.left {
  flex-direction: row;
}

.timeline-item.right {
  flex-direction: row-reverse;
}

.timeline-content {
  position: relative;
  background: white;
  border-radius: 1rem;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
  width: 45%;
  transition: all 0.5s ease;
  border-top: 4px solid;
}

.timeline-item.left .timeline-content {
  margin-right: 3rem;
}

.timeline-item.right .timeline-content {
  margin-left: 3rem;
}

.timeline-content.hovered {
  transform: scale(1.05);
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}

/* Colores de borde por tipo */
.color-burgundy {
  border-top-color: #6b4654 !important;
}
.color-gold {
  border-top-color: #d4af87 !important;
}
.color-terracotta {
  border-top-color: #c9756f !important;
}
.color-sage {
  border-top-color: #747f6e !important;
}

/* Year Badge */
.year-badge {
  position: absolute;
  top: -1rem;
  padding: 0.5rem 1.5rem;
  border-radius: 9999px;
  font-weight: bold;
  font-size: 0.875rem;
  color: white;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.timeline-item.left .year-badge {
  right: 1.5rem;
}

.timeline-item.right .year-badge {
  left: 1.5rem;
}

.badge-burgundy {
  background: linear-gradient(to right, #6b4654, #8b6b7a);
}
.badge-gold {
  background: linear-gradient(to right, #d4af87, #e6c9a8);
}
.badge-terracotta {
  background: linear-gradient(to right, #c9756f, #db9690);
}
.badge-sage {
  background: linear-gradient(to right, #747f6e, #919f8a);
}

/* Icon Wrapper - ESTILOS PARA ICONOS DE LUCIDE */
.icon-wrapper {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 3.5rem;
  height: 3.5rem;
  border-radius: 0.75rem;
  margin-bottom: 1rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.icon-lucide {
  color: white;
  stroke-width: 2;
}

.icon-burgundy {
  background: linear-gradient(to bottom right, #6b4654, #8b6b7a);
}
.icon-gold {
  background: linear-gradient(to bottom right, #d4af87, #e6c9a8);
}
.icon-terracotta {
  background: linear-gradient(to bottom right, #c9756f, #db9690);
}
.icon-sage {
  background: linear-gradient(to bottom right, #747f6e, #919f8a);
}

/* Text Content */
.item-title {
  font-size: 1.25rem;
  font-weight: bold;
  color: #6b4654;
  margin-bottom: 0.5rem;
}

.item-institution {
  font-size: 0.875rem;
  font-weight: 600;
  color: #c9756f;
  margin-bottom: 0.75rem;
}

.item-description {
  color: #8b8680;
  font-size: 0.875rem;
  line-height: 1.6;
}

.learn-more {
  display: inline-block;
  margin-top: 1rem;
  font-size: 0.875rem;
  font-weight: 600;
  color: #6b4654;
  text-decoration: none;
  transition: color 0.3s;
}

.learn-more:hover {
  color: #c9756f;
}

/* Timeline Dot */
.timeline-dot {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 1.5rem;
  height: 1.5rem;
  border-radius: 9999px;
  background: linear-gradient(to bottom right, #6b4654, #c9756f);
  border: 4px solid #f5f1ed;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
  z-index: 10;
}

.timeline-item:hover .timeline-dot {
  transform: translateX(-50%) scale(1.5);
}

.timeline-spacer {
  width: 45%;
}

/* Arrow Decorator */
.arrow-decorator {
  position: absolute;
  top: 50%;
  transform: translateY(-50%) rotate(45deg);
  width: 2rem;
  height: 2rem;
  background: white;
  border-top: 2px solid;
  border-right: 2px solid;
}

.arrow-right {
  right: -1rem;
  border-color: #6b4654;
}

.arrow-left {
  left: -1rem;
  border-color: #d4af87;
}

/* Footer Decoration */
.footer-decoration {
  margin-top: 4rem;
  text-align: center;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: white;
  padding: 0.75rem 1.5rem;
  border-radius: 9999px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  margin-left: 50%;
  transform: translateX(-50%);
}

.pulse-dot {
  width: 0.75rem;
  height: 0.75rem;
  border-radius: 9999px;
  background: #6b4654;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.footer-decoration span {
  color: #8b8680;
  font-size: 0.875rem;
  font-weight: 500;
}

/* Responsive - Móviles */
@media (max-width: 768px) {
  .timeline-line {
    display: none;
  }

  .timeline-item {
    flex-direction: column !important;
  }

  .timeline-content {
    width: 100% !important;
    margin: 0 !important;
  }

  .timeline-dot,
  .arrow-decorator {
    display: none;
  }

  .timeline-spacer {
    display: none;
  }

  .main-title {
    font-size: 2rem;
  }
}
</style>
