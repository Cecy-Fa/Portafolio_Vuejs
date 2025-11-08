<script setup>
import { ref, computed } from 'vue'
import {
  Smartphone,
  GraduationCap,
  FileText,
  ExternalLink,
  Github,
  Calendar,
} from 'lucide-vue-next'

const hoveredId = ref(null)
const selectedCategory = ref('all')

const projects = [
  {
    id: 1,
    title: 'Aplicación de Reservas para Restaurantes',
    year: '2023',
    category: 'mobile',
    image: '🍽️',
    iconComponent: Smartphone,
    description:
      'Creé una aplicación móvil con Flutter que permite a los usuarios reservar mesas en restaurantes locales.',
    technologies: ['Flutter', 'Dart', 'Firebase', 'Google Maps API'],
    gradient: 'from-[#C9756F] to-[#DB9690]',
    color: '#C9756F',
    stats: { users: '500+', rating: '4.8' },
    projectLink: 'http://www.youtube.com/',
    githubLink: 'https://github.com/tu-usuario',
  },
  {
    id: 2,
    title: 'Plataforma de E-learning',
    year: '2022',
    category: 'web',
    image: '📚',
    iconComponent: GraduationCap,
    description:
      'Diseñé y desarrollé una plataforma de educación en línea utilizando Django y React. Con diferentes funcionalidades.',
    technologies: ['Django', 'React', 'PostgreSQL', 'WebRTC'],
    gradient: 'from-[#D4AF87] to-[#E6C9A8]',
    color: '#D4AF87',
    stats: { students: '1200+', courses: '45' },
    projectLink: 'http://www.direccion.com/',
    githubLink: 'https://github.com/tu-usuario',
  },
  {
    id: 3,
    title: 'Blog Personal con CMS',
    year: '2022',
    category: 'web',
    image: '📝',
    iconComponent: FileText,
    description:
      'Construí un blog personal con un sistema de gestión de contenidos (CMS) personalizado en WordPress.',
    technologies: ['WordPress', 'PHP', 'MySQL', 'Custom Theme'],
    gradient: 'from-[#747F6E] to-[#919F8A]',
    color: '#747F6E',
    stats: { posts: '150+', views: '10K+' },
    projectLink: 'http://www.direccion.com/',
    githubLink: 'https://github.com/tu-usuario',
  },
  {
    id: 4,
    title: 'App de Gestión de Tareas',
    year: '2023',
    category: 'mobile',
    image: '✅',
    iconComponent: Smartphone,
    description:
      'Aplicación móvil multiplataforma para gestión de tareas y proyectos con sincronización en la nube.',
    technologies: ['React Native', 'Node.js', 'MongoDB', 'Redux'],
    gradient: 'from-[#6B4654] to-[#8B6B7A]',
    color: '#6B4654',
    stats: { downloads: '800+', rating: '4.6' },
    projectLink: 'http://www.direccion.com/',
    githubLink: 'https://github.com/tu-usuario',
  },
]

const categories = [
  { id: 'all', label: 'Todos', icon: '🎯' },
  { id: 'web', label: 'Web', icon: '🌐' },
  { id: 'mobile', label: 'Móvil', icon: '📱' },
]

const filteredProjects = computed(() => {
  return selectedCategory.value === 'all'
    ? projects
    : projects.filter((p) => p.category === selectedCategory.value)
})
</script>

<template>
  <div class="projects-section">
    <div class="container-projects">
      <!-- Header -->
      <div class="header-projects">
        <div class="title-wrapper-projects">
          <h2 class="main-title-projects">
            Proyectos Destacados
            <div class="title-underline-projects"></div>
          </h2>
        </div>
        <p class="subtitle-projects">
          Soluciones innovadoras que transforman ideas en experiencias digitales
        </p>
      </div>

      <!-- Category Filter -->
      <div class="category-filter">
        <button
          v-for="cat in categories"
          :key="cat.id"
          @click="selectedCategory = cat.id"
          :class="['category-btn', { active: selectedCategory === cat.id }]"
        >
          <span class="category-icon">{{ cat.icon }}</span>
          {{ cat.label }}
        </button>
      </div>

      <!-- Projects Grid -->
      <div class="projects-grid">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="project-card"
          @mouseenter="hoveredId = project.id"
          @mouseleave="hoveredId = null"
        >
          <!-- Gradient Header -->
          <div :class="['project-header', 'bg-gradient-to-br', project.gradient]">
            <!-- Decorative circles -->
            <div class="deco-circle-top"></div>
            <div class="deco-circle-bottom"></div>

            <!-- Project Image/Emoji -->
            <div class="project-emoji">{{ project.image }}</div>

            <!-- Year Badge -->
            <div class="year-badge-project">
              <component :is="Calendar" :size="14" class="text-white" />
              <span>{{ project.year }}</span>
            </div>
          </div>

          <!-- Content -->
          <div class="project-content">
            <!-- Icon & Title -->
            <div class="project-title-section">
              <div
                class="project-icon-wrapper"
                :style="{
                  background: `linear-gradient(135deg, ${project.color}dd, ${project.color})`,
                }"
              >
                <component
                  :is="project.iconComponent"
                  :size="24"
                  :stroke-width="2"
                  class="text-white"
                />
              </div>
              <div class="project-title-text">
                <h3 class="project-title">{{ project.title }}</h3>
              </div>
            </div>

            <!-- Description -->
            <p class="project-description">{{ project.description }}</p>

            <!-- Stats -->
            <div class="project-stats">
              <div v-for="(value, key) in project.stats" :key="key" class="stat-item-project">
                <div class="stat-value" :style="{ color: project.color }">
                  {{ value }}
                </div>
                <div class="stat-label-project">{{ key }}</div>
              </div>
            </div>

            <!-- Technologies -->
            <div class="tech-tags">
              <span v-for="(tech, index) in project.technologies" :key="index" class="tech-tag">
                {{ tech }}
              </span>
            </div>

            <!-- Action Buttons -->
            <div class="action-buttons">
              :href="project.projectLink" target="_blank" class="btn-primary" :style="{ background:
              `linear-gradient(to right, ${project.color}, ${project.color}dd)` }" >
              <component :is="ExternalLink" :size="16" />
              Ver Proyecto
              <a :href="project.githubLink" target="_blank" class="btn-secondary">
                <component :is="Github" :size="20" />
              </a>
            </div>
          </div>

          <!-- Hover Border Effect -->
          <div
            :class="['hover-border', { active: hoveredId === project.id }]"
            :style="{ borderColor: project.color }"
          ></div>
        </div>
      </div>

      <!-- CTA Section -->
      <div class="cta-section">
        <h3 class="cta-title">¿Tienes un proyecto en mente?</h3>
        <p class="cta-subtitle">Trabajemos juntos para convertir tu idea en realidad</p>
        <button class="cta-button">Contáctame</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
/*Estilo de fondo de la galeria con un fondo estatico */
/* .galeria {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
    background-image: url('/src/assets/fondo-proyectos.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
} */

/* Estilos Fondo Animado de Css de la galería */
/* La clase 'galeria' es el contenedor principal de la galería de proyectos */
.galeria {
  /* Establece el ancho de la galería al 100% del contenedor padre */
  width: 100%;
  /* Establece la altura de la galería al 100% del contenedor padre */
  height: 100%;
  /* Utiliza flexbox para organizar los elementos hijos en la galería */
  display: flex;
  /* Permite que los elementos se ajusten y pasen a la siguiente línea si no caben en una sola fila */
  flex-wrap: wrap;
  /* Establece un espacio de 20px entre los elementos de la galería */
  gap: 20px;
  /* Agrega un padding de 20px alrededor de la galería */
  padding: 20px;
  /* Centra los elementos hijos horizontalmente */
  justify-content: center;
  /* Aplica un fondo con un degradado de colores */
  background: linear-gradient(-45deg, #021526, #03346e, #6eacda, #e2e2b6);
  /* Ajusta el tamaño del fondo para que cubra el área completa */
  background-size: 400% 400%;
  /* Aplica una animación al fondo que dura 15 segundos, tiene una transición suave y se repite infinitamente */
  animation: gradient 15s ease infinite;
}

/* Define una animación llamada 'gradient' para cambiar la posición del fondo */
@keyframes gradient {
  /* Al inicio, el fondo está posicionado en el 0% horizontal y 50% vertical */
  0% {
    background-position: 0% 50%;
  }

  /* A la mitad de la animación, el fondo se desplaza al 100% horizontal y 50% vertical */
  50% {
    background-position: 100% 50%;
  }

  /* Al final, el fondo vuelve a la posición inicial */
  100% {
    background-position: 0% 50%;
  }
}

/* La clase 'proyecto' es el contenedor individual de cada proyecto */
.proyecto {
  /* Utiliza flexbox para organizar el contenido del proyecto en una columna */
  display: flex;
  /* Establece la dirección de los elementos en columna */
  flex-direction: column;
  /* Aplica un borde de 2px sólido y color gris claro (#ddd) alrededor del proyecto */
  border: 2px solid #ddd;
  /* Redondea las esquinas del contenedor */
  border-radius: 8px;
  /* Oculta cualquier contenido que se desborde del contenedor */
  overflow: hidden;
  /* Establece un color de fondo claro para el proyecto */
  background-color: #f9f9f9;
  /* Define el ancho máximo del proyecto en 222px */
  max-width: 222px;
  /* Hace que el contenedor se ajuste flexiblemente ocupando al menos 300px de ancho */
  flex: 1 1 300px;
}

/* Estilo para las imágenes dentro del contenedor 'proyecto' */
.proyecto img {
  /* Hace que la imagen ocupe el 100% del ancho del contenedor */
  width: 100%;
  /* Mantiene la relación de aspecto de la imagen */
  height: auto;
  /* Asegura que la imagen se muestre como un bloque, sin espacio en línea alrededor */
  display: block;
}

/* La clase 'proyecto-info' contiene la información del proyecto */
.proyecto-info {
  /* Agrega un padding de 15px alrededor de la información */
  padding: 15px;
  /* Centra el texto dentro del contenedor */
  text-align: center;
}

/* Estilo para los títulos de los proyectos */
.proyecto-info h3 {
  /* Establece un margen superior e inferior de 10px */
  margin: 10px 0;
  /* Define el tamaño de la fuente a 1.3em (relativo al tamaño de fuente del contenedor) */
  font-size: 1.3em;
  /* Aplica un color gris oscuro (#333) al texto */
  color: #333;
}

/* Estilo para los párrafos de los proyectos */
.proyecto-info p {
  /* Establece un margen superior e inferior de 10px */
  margin: 10px 0;
  /* Define el tamaño de la fuente a 1em (igual al tamaño de fuente base) */
  font-size: 1em;
  /* Aplica un color gris (#666) al texto */
  color: #666;
}

/* La clase 'proyecto-links' organiza los enlaces y botones del proyecto */
.proyecto-links {
  /* Utiliza flexbox para organizar los enlaces en una columna */
  display: flex;
  /* Establece la dirección de los elementos en columna */
  flex-direction: column;
  /* Establece un espacio de 10px entre los elementos */
  gap: 10px;
  /* Agrega un margen superior de 10px */
  margin-top: 30px;
}

/* Estilo para el botón 'Ver Más' dentro de la clase 'proyecto-links' */
.proyecto-links .btn-ver-mas {
  /* Aplica un color de fondo azul (#007BFF) */
  background-color: #007bff;
  /* Aplica un color de texto blanco */
  color: #fff;
  /* Agrega un padding de 10px en vertical y 15px en horizontal */
  padding: 10px 15px;
  /* Redondea las esquinas del botón */
  border-radius: 5px;
  /* Elimina el subrayado del texto */
  text-decoration: none;
  /* Aplica una transición suave al cambiar el color de fondo */
  transition: background-color 0.3s;
  margin-top: 1rem;
}

/* Estilo para cuando el botón 'Ver Más' es hover */
.proyecto-links .btn-ver-mas:hover {
  /* Cambia el color de fondo a un azul más oscuro (#0056b3) */
  background-color: #0056b3;
}

/* Estilo para el enlace a GitHub dentro de la clase 'proyecto-links' */
.proyecto-links .github-link {
  /* Aplica un color gris oscuro (#333) al texto */
  color: #333;
  /* Elimina el subrayado del texto */
  text-decoration: none;
  /* Establece el tamaño de fuente a 0.9em (un poco más pequeño que el tamaño base) */
  font-size: 0.9em;
}

/* Estilo para cuando el enlace a GitHub es hover */
.proyecto-links .github-link:hover {
  /* Añade un subrayado al texto */
  text-decoration: underline;
}

/* ========================================
  ESTILOS PARA SECCIÓN DE PROYECTOS
   ======================================== */

.projects-section {
  min-height: 100vh;
  background-color: #f5f1ed;
  padding: 4rem 1rem;
}

.container-projects {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 1rem;
}

/* Header */
.header-projects {
  text-align: center;
  margin-bottom: 3rem;
}

.title-wrapper-projects {
  display: inline-block;
}

.main-title-projects {
  font-size: 2.5rem;
  font-weight: bold;
  color: #6b4654;
  margin-bottom: 0.5rem;
  position: relative;
}

.title-underline-projects {
  position: absolute;
  bottom: -0.5rem;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(to right, #c9756f, #d4af87, #747f6e);
  border-radius: 9999px;
}

.subtitle-projects {
  color: #8b8680;
  margin-top: 1.5rem;
  font-size: 1.125rem;
  max-width: 42rem;
  margin-left: auto;
  margin-right: auto;
}

/* Category Filter */
.category-filter {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.category-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  border-radius: 9999px;
  font-weight: 600;
  font-size: 0.875rem;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  background: white;
  color: #6b4654;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.category-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

.category-btn.active {
  background: linear-gradient(to right, #6b4654, #8b6b7a);
  color: white;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  transform: scale(1.05);
}

.category-icon {
  font-size: 1.125rem;
}

/* Projects Grid */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

/* Project Card */
.project-card {
  position: relative;
  background: white;
  border-radius: 1.5rem;
  overflow: hidden;
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
  transition: all 0.5s ease;
}

.project-card:hover {
  transform: translateY(-0.5rem);
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}

/* Project Header */
.project-header {
  position: relative;
  height: 12rem;
  padding: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.deco-circle-top {
  position: absolute;
  top: -4rem;
  right: -4rem;
  width: 8rem;
  height: 8rem;
  background: white;
  opacity: 0.1;
  border-radius: 9999px;
}

.deco-circle-bottom {
  position: absolute;
  bottom: -3rem;
  left: -3rem;
  width: 6rem;
  height: 6rem;
  background: white;
  opacity: 0.1;
  border-radius: 9999px;
}

.project-emoji {
  font-size: 5rem;
  z-index: 10;
  transition: all 0.5s ease;
}

.project-card:hover .project-emoji {
  transform: scale(1.1) rotate(3deg);
}

/* Year Badge */
.year-badge-project {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  padding: 0.25rem 1rem;
  border-radius: 9999px;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.year-badge-project span {
  color: white;
  font-size: 0.875rem;
  font-weight: 600;
}

/* Project Content */
.project-content {
  padding: 1.5rem;
}

/* Title Section */
.project-title-section {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  margin-bottom: 1rem;
}

.project-icon-wrapper {
  flex-shrink: 0;
  width: 3rem;
  height: 3rem;
  border-radius: 0.75rem;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.project-title-text {
  flex: 1;
}

.project-title {
  font-size: 1.25rem;
  font-weight: bold;
  color: #6b4654;
  margin: 0;
  line-height: 1.3;
}

/* Description */
.project-description {
  color: #8b8680;
  font-size: 0.875rem;
  line-height: 1.6;
  margin-bottom: 1rem;
}

/* Stats */
.project-stats {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #ebe6e0;
}

.stat-item-project {
  flex: 1;
}

.stat-value {
  font-size: 1.125rem;
  font-weight: bold;
  margin-bottom: 0.25rem;
}

.stat-label-project {
  font-size: 0.75rem;
  color: #8b8680;
  text-transform: capitalize;
}

/* Technology Tags */
.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-tag {
  padding: 0.25rem 0.75rem;
  background: #f5f1ed;
  color: #6b4654;
  border-radius: 9999px;
  font-size: 0.75rem;
  font-weight: 500;
  border: 1px solid #ebe6e0;
}

/* Action Buttons */
.action-buttons {
  display: flex;
  gap: 0.75rem;
}

.btn-primary {
  flex: 1;
  padding: 0.75rem;
  border-radius: 0.75rem;
  font-weight: 600;
  font-size: 0.875rem;
  color: white;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  text-decoration: none;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.btn-primary:hover {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  transform: translateY(-2px);
}

.btn-secondary {
  padding: 0.75rem 1rem;
  background: #f5f1ed;
  border-radius: 0.75rem;
  font-weight: 600;
  font-size: 0.875rem;
  color: #6b4654;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.btn-secondary:hover {
  background: #ebe6e0;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  transform: translateY(-2px);
}

/* Hover Border Effect */
.hover-border {
  position: absolute;
  inset: 0;
  border: 4px solid transparent;
  border-radius: 1.5rem;
  pointer-events: none;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.hover-border.active {
  opacity: 1;
}

/* CTA Section */
.cta-section {
  background: linear-gradient(to right, #6b4654, #8b6b7a);
  border-radius: 1.5rem;
  padding: 3rem;
  text-align: center;
}

.cta-title {
  font-size: 2rem;
  font-weight: bold;
  color: white;
  margin-bottom: 1rem;
}

.cta-subtitle {
  color: rgba(255, 255, 255, 0.8);
  font-size: 1.125rem;
  margin-bottom: 1.5rem;
  max-width: 42rem;
  margin-left: auto;
  margin-right: auto;
}

.cta-button {
  padding: 1rem 2rem;
  background: white;
  color: #6b4654;
  border-radius: 9999px;
  font-weight: bold;
  font-size: 1.125rem;
  border: none;
  cursor: pointer;
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.cta-button:hover {
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  transform: scale(1.05);
}

/* Utilities */
.text-white {
  color: white;
}

/* Tailwind-like gradient classes */
.bg-gradient-to-br {
  background-image: linear-gradient(to bottom right, var(--tw-gradient-stops));
}

.from-\[\#C9756F\] {
  --tw-gradient-from: #c9756f;
  --tw-gradient-stops: var(--tw-gradient-from), var(--tw-gradient-to, rgba(201, 117, 111, 0));
}

.to-\[\#DB9690\] {
  --tw-gradient-to: #db9690;
}

.from-\[\#D4AF87\] {
  --tw-gradient-from: #d4af87;
  --tw-gradient-stops: var(--tw-gradient-from), var(--tw-gradient-to, rgba(212, 175, 135, 0));
}

.to-\[\#E6C9A8\] {
  --tw-gradient-to: #e6c9a8;
}

.from-\[\#747F6E\] {
  --tw-gradient-from: #747f6e;
  --tw-gradient-stops: var(--tw-gradient-from), var(--tw-gradient-to, rgba(116, 127, 110, 0));
}

.to-\[\#919F8A\] {
  --tw-gradient-to: #919f8a;
}

.from-\[\#6B4654\] {
  --tw-gradient-from: #6b4654;
  --tw-gradient-stops: var(--tw-gradient-from), var(--tw-gradient-to, rgba(107, 70, 84, 0));
}

.to-\[\#8B6B7A\] {
  --tw-gradient-to: #8b6b7a;
}

/* Responsive */
@media (max-width: 768px) {
  .main-title-projects {
    font-size: 2rem;
  }

  .projects-grid {
    grid-template-columns: 1fr;
  }

  .cta-section {
    padding: 2rem;
  }

  .cta-title {
    font-size: 1.5rem;
  }
}

@media (min-width: 768px) {
  .main-title-projects {
    font-size: 3rem;
  }

  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
