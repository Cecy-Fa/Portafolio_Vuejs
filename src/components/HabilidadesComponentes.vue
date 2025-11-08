<script setup>
import { ref } from 'vue'
import { Code, Layers, Wrench, Database, Globe } from 'lucide-vue-next'

const hoveredSkill = ref(null)

const skillsData = {
  languages: {
    title: 'Lenguajes de Programación',
    iconComponent: Code,
    color: '#C9756F',
    skills: [
      { name: 'JavaScript', level: 'Intermedio', icon: '⚡' },
      { name: 'Python', level: 'Intermedio', icon: '🐍' },
      { name: 'HTML/CSS', level: 'Intermedio', icon: '🎨' },
      { name: 'Java', level: 'Intermedio', icon: '☕' },
      { name: 'SQL', level: 'Intermedio', icon: '📊' },
    ],
  },
  frameworks: {
    title: 'Frameworks y Librerías',
    iconComponent: Layers,
    color: '#D4AF87',
    skills: [
      { name: 'React.js', level: 'Intermedio', icon: '⚛️' },
      { name: 'Vue.js', level: 'Intermedio', icon: '💚' },
      { name: 'Node.js', level: 'Intermedio', icon: '🟢' },
      { name: 'Django', level: 'Intermedio', icon: '🎸' },
      { name: 'Bootstrap', level: 'Intermedio', icon: '🅱️' },
    ],
  },
  tools: {
    title: 'Herramientas y Software',
    iconComponent: Wrench,
    color: '#747F6E',
    skills: [
      { name: 'Git', level: 'Intermedio', icon: '🔀' },
      { name: 'Docker', level: 'Intermedio', icon: '🐋' },
      { name: 'Cypress', level: 'Intermedio', icon: '🧪' },
      { name: 'Figma', level: 'Intermedio', icon: '🎨' },
      { name: 'VS Code', level: 'Intermedio', icon: '💻' },
    ],
  },
  databases: {
    title: 'Bases de Datos',
    iconComponent: Database,
    color: '#6B4654',
    skills: [
      { name: 'MongoDB', level: 'Intermedio', icon: '🍃' },
      { name: 'MySQL', level: 'Intermedio', icon: '🐬' },
      { name: 'PostgreSQL', level: 'Intermedio', icon: '🐘' },
    ],
  },
  languages_spoken: {
    title: 'Idiomas',
    iconComponent: Globe,
    color: '#C9756F',
    skills: [
      { name: 'Español', level: 'Intermedio', icon: '🇦🇷' },
      { name: 'Inglés', level: 'Intermedio', icon: '🇺🇸' },
    ],
  },
}
</script>

<template>
  <div class="skills-section">
    <div class="container-skills">
      <!-- Header -->
      <div class="header-skills">
        <div class="title-wrapper-skills">
          <h2 class="main-title-skills">
            Habilidades
            <div class="title-underline-skills"></div>
          </h2>
        </div>
        <p class="subtitle-skills">Herramientas y tecnologías que domino</p>
      </div>

      <!-- Skills Categories -->
      <div class="categories-wrapper">
        <div v-for="(category, key) in skillsData" :key="key" class="category-container">
          <!-- Category Header -->
          <div class="category-header">
            <div
              class="category-icon-wrapper"
              :style="{
                background: `linear-gradient(135deg, ${category.color}dd, ${category.color})`,
              }"
            >
              <component
                :is="category.iconComponent"
                :size="24"
                :stroke-width="2.5"
                class="text-white"
              />
            </div>
            <h3 class="category-title">{{ category.title }}</h3>
          </div>

          <!-- Skills Grid -->
          <div class="skills-grid">
            <div
              v-for="(skill, index) in category.skills"
              :key="index"
              class="skill-badge"
              :style="{ borderLeftColor: category.color }"
              @mouseenter="hoveredSkill = `${key}-${index}`"
              @mouseleave="hoveredSkill = null"
            >
              <!-- Icon -->
              <div class="skill-icon">{{ skill.icon }}</div>

              <!-- Skill Name -->
              <div class="skill-name">{{ skill.name }}</div>

              <!-- Level -->
              <div class="skill-level" :style="{ color: category.color }">
                {{ skill.level }}
              </div>

              <!-- Hover effect bar -->
              <div
                :class="['skill-hover-bar', { active: hoveredSkill === `${key}-${index}` }]"
                :style="{ background: category.color }"
              ></div>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom Decoration -->
      <div class="bottom-decoration">
        <div class="decoration-badge">
          <div class="pulse-dot"></div>
          <span>Siempre aprendiendo nuevas tecnologías</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.skills-contenedor {
  padding: 2rem;
  /*Fondo cargado desde una imagen estatica en Assets*/
  /* background-image: url('/src/assets/fondo-proyectos.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat; */
  /*Fondo con gradiente*/
  background: linear-gradient(-45deg, #021526, #03346e, #6eacda, #e2e2b6);
  /*Fondo con color solido*/
  /* background-color: rgb(28, 41, 52); */
}

.skills-categoria {
  margin-bottom: 20px;
}

.skills-categoria h3 {
  display: flex;
  justify-content: left;
  margin-bottom: 10px;
  font-size: 1.5em;
  color: aliceblue;
  font-size: 1.5em;
  font-weight: bold;
}

.skills {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
  gap: 20px;
}

.skill {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
  background-color: rgba(241, 245, 243, 0.856);
  padding: 0.3em;
  border-radius: 8px;
  box-shadow: 0px 4px 12px rgba(2, 151, 151, 0.963);
  flex: 1 1 200px;
  max-width: 250px;
}

.skill:hover {
  background-color: rgba(2, 151, 151, 0.963);
}

.skill img {
  width: 35px;
  height: 35px;
}

.skill span {
  font-size: 1em;
  color: #333;
}

.skill:hover {
  font-size: 1.3em;
  transition: 2s ease;
}

@media (max-width: 768px) {
  .skills-categoria h3 {
    justify-content: center;
  }

  .skill {
    justify-content: center;
  }
}
/* ========================================
  ESTILOS PARA SECCIÓN DE HABILIDADES
  ======================================== */

.skills-section {
  min-height: 100vh;
  background-color: #f5f1ed;
  padding: 4rem 1rem;
}

.container-skills {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 1rem;
}

/* Header */
.header-skills {
  text-align: center;
  margin-bottom: 3rem;
}

.title-wrapper-skills {
  display: inline-block;
}

.main-title-skills {
  font-size: 2.5rem;
  font-weight: bold;
  color: #6b4654;
  margin-bottom: 0.5rem;
  position: relative;
}

.title-underline-skills {
  position: absolute;
  bottom: -0.5rem;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(to right, #c9756f, #d4af87, #747f6e);
  border-radius: 9999px;
}

.subtitle-skills {
  color: #8b8680;
  margin-top: 1.5rem;
  font-size: 1.125rem;
}

/* Categories Wrapper */
.categories-wrapper {
  display: flex;
  flex-direction: column;
  gap: 3rem;
}

/* Category Container */
.category-container {
  background: white;
  border-radius: 1.5rem;
  padding: 2rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.category-container:hover {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}

/* Category Header */
.category-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1.5rem;
}

.category-icon-wrapper {
  width: 3rem;
  height: 3rem;
  border-radius: 0.75rem;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  flex-shrink: 0;
}

.text-white {
  color: white;
}

.category-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #6b4654;
  margin: 0;
}

/* Skills Grid */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
}

/* Skill Badge */
.skill-badge {
  position: relative;
  background: white;
  border-radius: 0.75rem;
  padding: 1.25rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
  border-left: 4px solid;
  overflow: hidden;
}

.skill-badge:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
}

/* Skill Icon */
.skill-icon {
  font-size: 2rem;
  margin-bottom: 0.75rem;
  text-align: center;
}

/* Skill Name */
.skill-name {
  font-size: 1rem;
  font-weight: 600;
  color: #6b4654;
  margin-bottom: 0.5rem;
  text-align: center;
}

/* Skill Level */
.skill-level {
  font-size: 0.75rem;
  font-weight: 600;
  text-align: center;
}

/* Hover Bar Effect */
.skill-hover-bar {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3px;
  width: 0;
  transition: width 0.3s ease;
}

.skill-hover-bar.active {
  width: 100%;
}

/* Bottom Decoration */
.bottom-decoration {
  margin-top: 4rem;
  text-align: center;
}

.decoration-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: white;
  padding: 0.75rem 1.5rem;
  border-radius: 9999px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.pulse-dot {
  width: 0.75rem;
  height: 0.75rem;
  border-radius: 9999px;
  background: #c9756f;
  animation: pulse-animation 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

.decoration-badge span {
  color: #8b8680;
  font-size: 0.875rem;
  font-weight: 500;
}

/* Animation */
@keyframes pulse-animation {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

/* Responsive - Tablet */
@media (min-width: 640px) {
  .skills-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* Responsive - Desktop Small */
@media (min-width: 1024px) {
  .main-title-skills {
    font-size: 3rem;
  }

  .skills-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

/* Responsive - Desktop Large */
@media (min-width: 1280px) {
  .skills-grid {
    grid-template-columns: repeat(5, 1fr);
  }
}

/* Responsive - Mobile */
@media (max-width: 639px) {
  .category-container {
    padding: 1.5rem;
  }

  .skills-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 0.75rem;
  }

  .skill-badge {
    padding: 1rem;
  }

  .skill-icon {
    font-size: 1.5rem;
  }

  .skill-name {
    font-size: 0.875rem;
  }

  .main-title-skills {
    font-size: 2rem;
  }

  .category-title {
    font-size: 1.25rem;
  }
}
</style>
