<script setup>
import { ref } from 'vue'
import { TrendingUp, Code, Shield, Layout, GitBranch, Award } from 'lucide-vue-next'

const hoveredId = ref(null)

const experienceData = {
  title: 'DESARROLLADOR FULL STACK',
  period: 'Desde Enero 2022 / Julio 2024',
  company: 'Tech Solutions Inc.',
  achievements: [
    {
      id: 1,
      iconComponent: TrendingUp,
      title: 'Liderazgo de Equipo',
      description:
        'Lideré un equipo de 5 desarrolladores en la creación de una plataforma de comercio electrónico que incrementó las ventas en un 35% durante el primer año.',
      metric: '+35%',
      color: '#C9756F',
    },
    {
      id: 2,
      iconComponent: Code,
      title: 'Desarrollo Web Avanzado',
      description:
        'Diseñé y desarrollé aplicaciones web utilizando Node.js, React y MongoDB, logrando reducir el tiempo de carga de las páginas.',
      metric: '70%',
      color: '#D4AF87',
    },
    {
      id: 3,
      iconComponent: Shield,
      title: 'Seguridad & Autenticación',
      description:
        'Implementé soluciones de autenticación y autorización, mejorando la seguridad del sitio web y reduciendo los intentos de acceso no autorizado en un 20%.',
      metric: '-20%',
      color: '#747F6E',
    },
    {
      id: 4,
      iconComponent: Layout,
      title: 'Diseño UX/UI',
      description:
        'Colaboré con diseñadores de UX/UI para crear interfaces de usuario atractivas y fáciles de usar, aumentando la satisfacción del cliente en un 15%.',
      metric: '+15%',
      color: '#6B4654',
    },
    {
      id: 5,
      iconComponent: GitBranch,
      title: 'CI/CD & DevOps',
      description:
        'Automaticé procesos de despliegue continuo utilizando Jenkins y Docker, reduciendo los tiempos de despliegue en un 40%.',
      metric: '40%',
      color: '#C9756F',
    },
  ],
}

const techStack = [
  'Node.js',
  'React',
  'MongoDB',
  'Docker',
  'Jenkins',
  'Git',
  'AWS',
  'JavaScript',
  'TypeScript',
]
</script>

<template>
  <div class="experience-section">
    <div class="container-exp">
      <!-- Header -->
      <div class="header-exp">
        <div class="title-wrapper-exp">
          <h2 class="main-title-exp">
            Experiencia Profesional
            <div class="title-underline-exp"></div>
          </h2>
        </div>
        <p class="subtitle-exp">Transformando ideas en soluciones digitales de alto impacto</p>
      </div>

      <!-- Main Experience Card -->
      <div class="main-card">
        <!-- Decorative Elements -->
        <div class="deco-circle deco-1"></div>
        <div class="deco-circle deco-2"></div>

        <div class="main-card-content">
          <!-- Badge -->
          <div class="badge-highlight">
            <component :is="Award" :size="20" class="text-gold" />
            <span>Posición Destacada</span>
          </div>

          <!-- Title -->
          <h3 class="job-title">{{ experienceData.title }}</h3>

          <!-- Period -->
          <div class="period-container">
            <div class="pulse-indicator"></div>
            <p class="period-text">{{ experienceData.period }}</p>
          </div>

          <!-- Company -->
          <p class="company-name">{{ experienceData.company }}</p>

          <!-- Stats Bar -->
          <div class="stats-grid">
            <div class="stat-item">
              <div class="stat-number stat-gold">5</div>
              <div class="stat-label">Proyectos</div>
            </div>
            <div class="stat-item">
              <div class="stat-number stat-terracotta">2.5</div>
              <div class="stat-label">Años</div>
            </div>
            <div class="stat-item">
              <div class="stat-number stat-sage">10+</div>
              <div class="stat-label">Tecnologías</div>
            </div>
            <div class="stat-item">
              <div class="stat-number stat-white">100%</div>
              <div class="stat-label">Dedicación</div>
            </div>
          </div>
        </div>
      </div>

      <!-- Achievements Grid -->
      <div class="achievements-section">
        <h4 class="achievements-title">
          <div class="title-bar"></div>
          Logros Principales
        </h4>

        <div class="achievements-grid">
          <div
            v-for="achievement in experienceData.achievements"
            :key="achievement.id"
            class="achievement-card"
            :style="{ borderTopColor: achievement.color }"
            @mouseenter="hoveredId = achievement.id"
            @mouseleave="hoveredId = null"
          >
            <!-- Metric Badge -->
            <div class="metric-badge" :style="{ background: achievement.color }">
              {{ achievement.metric }}
            </div>

            <!-- Icon -->
            <div
              class="achievement-icon"
              :style="{
                background: `linear-gradient(135deg, ${achievement.color}dd, ${achievement.color})`,
              }"
            >
              <component
                :is="achievement.iconComponent"
                :size="28"
                :stroke-width="2"
                class="icon-white"
              />
            </div>

            <!-- Title -->
            <h5 class="achievement-title">{{ achievement.title }}</h5>

            <!-- Description -->
            <p class="achievement-description">{{ achievement.description }}</p>

            <!-- Hover Effect Bar -->
            <div
              class="hover-bar"
              :class="{ active: hoveredId === achievement.id }"
              :style="{ background: achievement.color }"
            ></div>
          </div>
        </div>
      </div>

      <!-- Tech Stack Section -->
      <div class="tech-stack-section">
        <h4 class="tech-stack-title">Stack Tecnológico Principal</h4>

        <div class="tech-stack-grid">
          <div v-for="(tech, index) in techStack" :key="index" class="tech-badge">
            {{ tech }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  padding: 2rem;
  background-color: rgb(28, 41, 52);
  border-radius: 15px;
}

.titulo {
  font-size: 1.5rem;
  color: coral;
}

.fecha {
  font-size: 1rem;
  color: burlywood;
  margin-bottom: 1rem;
}

.listado {
  display: flex;
  flex-direction: column;
}

.item {
  align-items: center;
  display: flex;
  padding: 1rem;
  gap: 1.5rem;
}
/* ========================================
  ESTILOS PARA SECCIÓN DE EXPERIENCIA
   ======================================== */

.experience-section {
  min-height: 100vh;
  background-color: #f5f1ed;
  padding: 4rem 1rem;
}

.container-exp {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 1rem;
}

/* Header */
.header-exp {
  text-align: center;
  margin-bottom: 4rem;
}

.title-wrapper-exp {
  display: inline-block;
}

.main-title-exp {
  font-size: 2.5rem;
  font-weight: bold;
  color: #6b4654;
  margin-bottom: 0.5rem;
  position: relative;
}

.title-underline-exp {
  position: absolute;
  bottom: -0.5rem;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(to right, #c9756f, #d4af87, #747f6e);
  border-radius: 9999px;
}

.subtitle-exp {
  color: #8b8680;
  margin-top: 1.5rem;
  font-size: 1.125rem;
}

/* Main Experience Card */
.main-card {
  background: linear-gradient(to bottom right, #6b4654, #4a3038);
  border-radius: 1.5rem;
  padding: 3rem;
  margin-bottom: 3rem;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  position: relative;
  overflow: hidden;
}

/* Decorative Circles */
.deco-circle {
  position: absolute;
  border-radius: 9999px;
  opacity: 0.1;
}

.deco-1 {
  top: -8rem;
  right: -8rem;
  width: 16rem;
  height: 16rem;
  background-color: #c9756f;
}

.deco-2 {
  bottom: -6rem;
  left: -6rem;
  width: 12rem;
  height: 12rem;
  background-color: #d4af87;
}

.main-card-content {
  position: relative;
  z-index: 10;
}

/* Badge Highlight */
.badge-highlight {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  padding: 0.5rem 1rem;
  border-radius: 9999px;
  margin-bottom: 1.5rem;
}

.badge-highlight span {
  color: white;
  font-size: 0.875rem;
  font-weight: 600;
}

.text-gold {
  color: #d4af87;
}

/* Job Title */
.job-title {
  font-size: 2rem;
  font-weight: bold;
  color: white;
  margin-bottom: 0.75rem;
}

/* Period */
.period-container {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1.5rem;
}

.pulse-indicator {
  width: 0.5rem;
  height: 0.5rem;
  background-color: #d4af87;
  border-radius: 9999px;
  animation: pulse 2s infinite;
}

.period-text {
  color: #d4af87;
  font-size: 1.125rem;
  font-weight: 500;
}

/* Company Name */
.company-name {
  color: rgba(255, 255, 255, 0.8);
  font-size: 1.125rem;
  margin-bottom: 2rem;
}

/* Stats Grid */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border-radius: 1rem;
  padding: 1.5rem;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 0.25rem;
}

.stat-gold {
  color: #d4af87;
}
.stat-terracotta {
  color: #c9756f;
}
.stat-sage {
  color: #747f6e;
}
.stat-white {
  color: white;
}

.stat-label {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.875rem;
}

/* Achievements Section */
.achievements-section {
  margin-bottom: 3rem;
}

.achievements-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #6b4654;
  margin-bottom: 2rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.title-bar {
  width: 4px;
  height: 2rem;
  background: linear-gradient(to bottom, #c9756f, #d4af87);
  border-radius: 9999px;
}

/* Achievements Grid */
.achievements-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.achievement-card {
  position: relative;
  background: white;
  border-radius: 1rem;
  padding: 1.5rem;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  border-top: 4px solid;
  transition: all 0.5s ease;
  cursor: pointer;
}

.achievement-card:hover {
  transform: translateY(-0.5rem);
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}

/* Metric Badge */
.metric-badge {
  position: absolute;
  top: -0.75rem;
  right: -0.75rem;
  width: 4rem;
  height: 4rem;
  border-radius: 9999px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  color: white;
  font-size: 0.875rem;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

/* Achievement Icon */
.achievement-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 3.5rem;
  height: 3.5rem;
  border-radius: 0.75rem;
  margin-bottom: 1rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  transition: transform 0.5s ease;
}

.achievement-card:hover .achievement-icon {
  transform: scale(1.1);
}

.icon-white {
  color: white;
}

/* Achievement Text */
.achievement-title {
  font-size: 1.125rem;
  font-weight: bold;
  color: #6b4654;
  margin-bottom: 0.75rem;
}

.achievement-description {
  color: #8b8680;
  font-size: 0.875rem;
  line-height: 1.6;
}

/* Hover Bar */
.hover-bar {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 4px;
  width: 0;
  border-radius: 0 0 1rem 1rem;
  transition: width 0.5s ease;
}

.hover-bar.active {
  width: 100%;
}

/* Tech Stack Section */
.tech-stack-section {
  background: linear-gradient(to right, #f5f1ed, #ebe6e0);
  border-radius: 1.5rem;
  padding: 3rem;
}

.tech-stack-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #6b4654;
  margin-bottom: 1.5rem;
  text-align: center;
}

.tech-stack-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
}

.tech-badge {
  padding: 0.75rem 1.5rem;
  background: white;
  border-radius: 9999px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  color: #6b4654;
  font-weight: 600;
  font-size: 0.875rem;
  transition: all 0.3s ease;
  cursor: pointer;
}

.tech-badge:hover {
  transform: scale(1.05);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

/* Animations */
@keyframes pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

/* Responsive */
@media (max-width: 768px) {
  .main-title-exp {
    font-size: 2rem;
  }

  .job-title {
    font-size: 1.5rem;
  }

  .main-card {
    padding: 2rem;
  }

  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .achievements-grid {
    grid-template-columns: 1fr;
  }

  .tech-stack-section {
    padding: 2rem;
  }
}

@media (min-width: 768px) {
  .main-title-exp {
    font-size: 2.5rem;
  }

  .stats-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

@media (min-width: 1024px) {
  .achievements-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>
