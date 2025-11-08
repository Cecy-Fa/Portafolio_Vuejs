<style scoped></style>
<script setup>
import NavBar from './components/NavBar.vue'
import DatosPersonales from './components/DatosPersonales.vue'
import Educacion from './components/EducacionComponente.vue'
import ExperienciaComponentes from './components/ExperienciaComponentes.vue'
import ProyectosComponente from './components/ProyectosComponente.vue'

import InteresesComponentes from './components/InteresesComponentes.vue'
import HabilidadesComponentes from './components/HabilidadesComponentes.vue'

// Importa el componente del ícono de corazón
import { Heart } from 'lucide-vue-next'

// Define el año actual de forma dinámica
const currentYear = new Date().getFullYear()
</script>

<template>
  <header id="top">
    <!--Barra de Navegacion-->
    <NavBar />
    <!--Componente Datos Personales-->
    <DatosPersonales />
  </header>
  <main>
    <!--el estilo css de section se encuentra en base.css-->
    <section id="educacion">
      <!--Componente Educación-->
      <Educacion />
    </section>
    <section id="experiencia">
      <!--Componente Experiencia-->
      <ExperienciaComponentes />
    </section>
    <section id="proyectos">
      <!--Componente Proyectos-->
      <ProyectosComponente />
    </section>
    <section id="habilidades">
      <!--Componente Habilidades-->
      <HabilidadesComponentes />
    </section>
    <section id="intereses">
      <!--Componente Intereses-->
      <InteresesComponentes />
    </section>
  </main>

  <footer class="simple-footer-layout">
    <div class="top-separator">
      <div class="line-deco"></div>

      <div class="dot-decoration">
        <div class="dot"></div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>

      <div class="line-deco"></div>
    </div>

    <div class="middle-separator"></div>

    <div class="footer-content-simple">
      <p>© {{ currentYear }} Cecilia Farias</p>
      <p>Portafolio Web</p>
      <p>Tutorial UTN FRSR</p>

      <div class="made-with-simple">
        Hecho con <component :is="Heart" :size="14" class="heart-icon" /> en Argentina
      </div>
    </div>
  </footer>
</template>

<style scoped>
/* ---------------------------------------------------- */
/* Estilos generales del contenedor y color de fondo */
/* ---------------------------------------------------- */
.simple-footer-layout {
  /* Color de fondo oscuro de tu imagen */
  background-color: #6b4654;
  color: #d4af87; /* Color de texto claro */
  padding: 30px 20px;
  text-align: center;
  font-family: sans-serif; /* Ajusta a tu fuente real */
}

.footer-content-simple p {
  margin: 5px 0;
  font-size: 16px;
}

/* ---------------------------------------------------- */
/* Estilos para los divisores (líneas y puntos) */
/* ---------------------------------------------------- */
.top-separator {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
}

.line-deco {
  /* Simula la línea horizontal fina */
  flex-grow: 1;
  height: 1px;
  background-color: #d4af87; /* Color de línea claro */
  max-width: 40%;
  opacity: 0.5;
}

.dot-decoration {
  display: flex;
  gap: 8px; /* Espacio entre los puntos */
  margin: 0 10px;
}

.dot {
  /* Estilo de los puntos */
  width: 6px;
  height: 6px;
  background-color: #d4af87; /* Color de punto claro */
  border-radius: 50%;
}

.middle-separator {
  /* Simula la segunda línea horizontal fina (más abajo) */
  width: 100%;
  height: 1px;
  background-color: #d4af87;
  opacity: 0.2;
  margin: 30px auto;
}

/* ---------------------------------------------------- */
/* Estilos del icono de corazón */
/* ---------------------------------------------------- */
.made-with-simple {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 15px;
}

.heart-icon {
  margin: 0 5px;
  color: #e4405f; /* Un rojo más vibrante para el corazón */
}
</style>
