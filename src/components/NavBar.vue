<script setup>
import { ref } from 'vue'

const navegacion = ref([
  { id: 1, nombre: 'Educación', enlace: '#educacion', color: '#C9756F' },
  { id: 2, nombre: 'Experiencia', enlace: '#experiencia', color: '#D4AF87' },
  { id: 3, nombre: 'Proyectos', enlace: '#proyectos', color: '#747F6E' },
  { id: 4, nombre: 'Habilidades', enlace: '#habilidades', color: '#6B4654' },
  { id: 5, nombre: 'Intereses', enlace: '#intereses', color: '#C9756F' },
])

const activeSection = ref('')
</script>

<template>
  <nav class="navbar">
    <div class="navbar-container">
      <!-- Logo/Brand -->
      <div class="navbar-brand">
        <div class="brand-circle">FC</div>
        <span class="brand-text">Portfolio</span>
      </div>

      <!-- Navigation Menu -->
      <div class="navbar-menu">
        <a
          v-for="nav in navegacion"
          :key="nav.id"
          :href="nav.enlace"
          class="nav-item"
          :style="{ '--item-color': nav.color }"
        >
          {{ nav.nombre }}
        </a>
      </div>
    </div>
  </nav>
</template>

<style scoped>
/* Navbar Container */
.navbar {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: rgba(212, 175, 135, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  padding: 0.75rem 2rem;
  transition: all 0.3s ease;
}

.navbar-container {
  max-width: 1400px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Brand/Logo */
.navbar-brand {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.brand-circle {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: linear-gradient(135deg, #c9756f, #6b4654);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: bold;
  font-size: 0.9rem;
  box-shadow: 0 4px 10px rgba(107, 70, 84, 0.3);
  transition: transform 0.3s ease;
}

.brand-circle:hover {
  transform: scale(1.1) rotate(5deg);
}

.brand-text {
  font-weight: 700;
  font-size: 1.1rem;
  color: #6b4654;
  display: none;
}

/* Navigation Menu */
.navbar-menu {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}

.nav-item {
  color: #6b4654;
  text-decoration: none;
  padding: 0.6rem 1.25rem;
  border-radius: 0.5rem;
  font-weight: 500;
  font-size: 0.95rem;
  position: relative;
  transition: all 0.3s ease;
  border: 2px solid transparent;
  background: rgba(255, 255, 255, 0.3);
}

/* Hover Effect */
.nav-item:hover {
  background: white;
  color: var(--item-color);
  border-color: var(--item-color);
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

/* Active Effect */
.nav-item:active {
  transform: translateY(0);
}

/* Underline Animation */
.nav-item::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 3px;
  background: var(--item-color);
  border-radius: 9999px;
  transition: width 0.3s ease;
}

.nav-item:hover::after {
  width: 60%;
}

/* Responsive - Tablet */
@media (max-width: 1024px) {
  .navbar {
    padding: 0.75rem 1.5rem;
  }

  .navbar-menu {
    gap: 0.35rem;
  }

  .nav-item {
    padding: 0.5rem 1rem;
    font-size: 0.9rem;
  }
}

/* Responsive - Mobile */
@media (max-width: 768px) {
  .navbar {
    padding: 0.75rem 1rem;
  }

  .navbar-container {
    flex-direction: column;
    gap: 1rem;
  }

  .navbar-brand {
    width: 100%;
    justify-content: center;
  }

  .brand-text {
    display: inline;
  }

  .navbar-menu {
    width: 100%;
    justify-content: center;
    flex-wrap: wrap;
  }

  .nav-item {
    padding: 0.5rem 0.9rem;
    font-size: 0.85rem;
  }
}

@media (max-width: 480px) {
  .navbar-menu {
    gap: 0.25rem;
  }

  .nav-item {
    padding: 0.4rem 0.7rem;
    font-size: 0.8rem;
  }

  .brand-circle {
    width: 35px;
    height: 35px;
    font-size: 0.8rem;
  }

  .brand-text {
    font-size: 1rem;
  }
}
</style>
