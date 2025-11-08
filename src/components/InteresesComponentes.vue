<script setup>
import { Sparkles, Code, Bike, Lightbulb, Scissors } from 'lucide-vue-next'
</script>

<template>
  <div class="interests-simple-section">
    <!-- Animated Background -->
    <div class="animated-background">
      <!-- Floating shapes -->
      <div class="shape shape-1"></div>
      <div class="shape shape-2"></div>
      <div class="shape shape-3"></div>
      <div class="shape shape-4"></div>
      <div class="shape shape-5"></div>

      <!-- Gradient orbs -->
      <div class="orb orb-1"></div>
      <div class="orb orb-2"></div>
      <div class="orb orb-3"></div>

      <!-- Mesh gradient overlay -->
      <div class="mesh-gradient"></div>
    </div>

    <div class="content-wrapper">
      <!-- Floating Icons -->
      <div class="floating-icons">
        <div class="floating-icon icon-1">
          <component :is="Code" :size="24" class="icon-burgundy" />
        </div>
        <div class="floating-icon icon-2">
          <component :is="Bike" :size="24" class="icon-gold" />
        </div>
        <div class="floating-icon icon-3">
          <component :is="Lightbulb" :size="24" class="icon-sage" />
        </div>
        <div class="floating-icon icon-4">
          <component :is="Scissors" :size="24" class="icon-purple" />
        </div>
      </div>

      <!-- Main Content Card -->
      <div class="content-card">
        <!-- Decorative corner elements -->
        <div class="corner-decoration corner-top-left"></div>
        <div class="corner-decoration corner-top-right"></div>
        <div class="corner-decoration corner-bottom-left"></div>
        <div class="corner-decoration corner-bottom-right"></div>

        <!-- Sparkle icon -->
        <div class="sparkle-container">
          <component :is="Sparkles" :size="40" class="sparkle-icon" />
        </div>

        <!-- Title with gradient -->
        <h2 class="title-gradient">Intereses</h2>

        <!-- Divider -->
        <div class="divider-container">
          <div class="divider-line"></div>
          <div class="divider-dot"></div>
          <div class="divider-line"></div>
        </div>

        <!-- Main paragraph -->
        <p class="main-paragraph">
          Me apasiona el <strong>desarrollo de software de código abierto</strong>, donde colaboro
          activamente en proyectos de GitHub para optimizar herramientas ampliamente utilizadas.
          Disfruto practicar <strong>deportes al aire libre</strong> como el ciclismo, que me ayuda
          a mantener un equilibrio saludable entre el trabajo y la vida personal. Exploro
          constantemente las últimas <strong>tendencias tecnológicas</strong>, especialmente en
          inteligencia artificial, desarrollo de aplicaciones móviles y ciberseguridad. Las
          <strong>manualidades</strong>
          son mi hobby favorito, permitiéndome expresar mi creatividad y desconectarme del entorno
          digital.
        </p>

        <!-- Icon tags -->
        <div class="icon-tags">
          <div class="icon-tag tag-1">💻 <span>Código Abierto</span></div>
          <div class="icon-tag tag-2">🚴 <span>Ciclismo</span></div>
          <div class="icon-tag tag-3">🤖 <span>IA & Tech</span></div>
          <div class="icon-tag tag-4">✂️ <span>Manualidades</span></div>
        </div>
      </div>

      <!-- Bottom decoration -->
      <div class="bottom-decoration">
        <div class="decoration-line"></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.intereses-contenedor {
  display: flex;
  position: relative;
  margin: 0 auto;
  max-width: 85%;
  padding: 1rem;
}

.contenedor-lista {
  list-style-type: none;
  padding: 1rem;
  margin-bottom: 0.5rem;
  color: var(--vt-c-white-soft);
  font-size: 1.4rem;
  text-shadow: 3px 3px 6px rgba(0, 0, 0, 1);
}

.item {
  margin-bottom: 1rem;
}
/* ========================================
   ESTILOS PARA SECCIÓN DE INTERESES (SIMPLE)
   ======================================== */

.interests-simple-section {
  min-height: 100vh;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4rem 1rem;
}

/* Animated Background */
.animated-background {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, #f5f1ed 0%, #ebe6e0 50%, #f5f1ed 100%);
}

/* Floating Shapes */
.shape {
  position: absolute;
  border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
  opacity: 0.15;
  animation: morph 15s ease-in-out infinite;
}

.shape-1 {
  width: 300px;
  height: 300px;
  background: linear-gradient(45deg, #c9756f, #db9690);
  top: 10%;
  left: 5%;
  animation-delay: 0s;
}

.shape-2 {
  width: 200px;
  height: 200px;
  background: linear-gradient(45deg, #d4af87, #e6c9a8);
  top: 60%;
  right: 10%;
  animation-delay: 3s;
}

.shape-3 {
  width: 250px;
  height: 250px;
  background: linear-gradient(45deg, #747f6e, #919f8a);
  bottom: 15%;
  left: 15%;
  animation-delay: 6s;
}

.shape-4 {
  width: 180px;
  height: 180px;
  background: linear-gradient(45deg, #6b4654, #8b6b7a);
  top: 30%;
  right: 20%;
  animation-delay: 9s;
}

.shape-5 {
  width: 220px;
  height: 220px;
  background: linear-gradient(45deg, #c9756f, #d4af87);
  bottom: 40%;
  right: 5%;
  animation-delay: 12s;
}

@keyframes morph {
  0%,
  100% {
    border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
    transform: translate(0, 0) rotate(0deg);
  }
  25% {
    border-radius: 58% 42% 75% 25% / 76% 46% 54% 24%;
    transform: translate(20px, -20px) rotate(90deg);
  }
  50% {
    border-radius: 50% 50% 33% 67% / 55% 27% 73% 45%;
    transform: translate(-20px, 20px) rotate(180deg);
  }
  75% {
    border-radius: 33% 67% 58% 42% / 63% 68% 32% 37%;
    transform: translate(20px, 20px) rotate(270deg);
  }
}

/* Gradient Orbs */
.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.2;
  animation: float-orb 20s ease-in-out infinite;
}

.orb-1 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, #c9756f 0%, transparent 70%);
  top: -100px;
  right: -100px;
}

.orb-2 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, #d4af87 0%, transparent 70%);
  bottom: -150px;
  left: -150px;
  animation-delay: 7s;
}

.orb-3 {
  width: 350px;
  height: 350px;
  background: radial-gradient(circle, #747f6e 0%, transparent 70%);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation-delay: 14s;
}

@keyframes float-orb {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(50px, -50px);
  }
}

/* Mesh Gradient */
.mesh-gradient {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(at 20% 30%, rgba(201, 117, 111, 0.1) 0px, transparent 50%),
    radial-gradient(at 80% 70%, rgba(212, 175, 135, 0.1) 0px, transparent 50%),
    radial-gradient(at 50% 50%, rgba(116, 127, 110, 0.08) 0px, transparent 50%);
}

/* Content Wrapper */
.content-wrapper {
  max-width: 900px;
  width: 100%;
  position: relative;
  z-index: 10;
}

/* Floating Icons */
.floating-icons {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.floating-icon {
  position: absolute;
  background: white;
  padding: 1rem;
  border-radius: 1rem;
  box-shadow: 0 10px 30px -5px rgba(0, 0, 0, 0.1);
  animation: bounce-float 3s ease-in-out infinite;
}

.icon-1 {
  top: 10%;
  left: -50px;
  animation-delay: 0s;
}

.icon-2 {
  top: 20%;
  right: -40px;
  animation-delay: 0.5s;
}

.icon-3 {
  bottom: 30%;
  left: -60px;
  animation-delay: 1s;
}

.icon-4 {
  bottom: 20%;
  right: -50px;
  animation-delay: 1.5s;
}

.icon-burgundy {
  color: #c9756f;
}

.icon-gold {
  color: #d4af87;
}

.icon-sage {
  color: #747f6e;
}

.icon-purple {
  color: #6b4654;
}

@keyframes bounce-float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}

/* Content Card */
.content-card {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(20px);
  border-radius: 2rem;
  padding: 4rem;
  box-shadow:
    0 25px 50px -12px rgba(0, 0, 0, 0.15),
    0 0 0 1px rgba(255, 255, 255, 0.5);
  position: relative;
  border: 2px solid transparent;
  background-clip: padding-box;
}

.content-card::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 2rem;
  padding: 2px;
  background: linear-gradient(135deg, #c9756f, #d4af87, #747f6e, #6b4654);
  -webkit-mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  opacity: 0.3;
}

/* Corner Decorations */
.corner-decoration {
  position: absolute;
  width: 40px;
  height: 40px;
  opacity: 0.3;
}

.corner-top-left {
  top: 1rem;
  left: 1rem;
  border-top: 3px solid #c9756f;
  border-left: 3px solid #c9756f;
  border-radius: 1rem 0 0 0;
}

.corner-top-right {
  top: 1rem;
  right: 1rem;
  border-top: 3px solid #d4af87;
  border-right: 3px solid #d4af87;
  border-radius: 0 1rem 0 0;
}

.corner-bottom-left {
  bottom: 1rem;
  left: 1rem;
  border-bottom: 3px solid #747f6e;
  border-left: 3px solid #747f6e;
  border-radius: 0 0 0 1rem;
}

.corner-bottom-right {
  bottom: 1rem;
  right: 1rem;
  border-bottom: 3px solid #6b4654;
  border-right: 3px solid #6b4654;
  border-radius: 0 0 1rem 0;
}

/* Sparkle */
.sparkle-container {
  text-align: center;
  margin-bottom: 1.5rem;
}

.sparkle-icon {
  color: #c9756f;
  animation: sparkle 2s ease-in-out infinite;
}

@keyframes sparkle {
  0%,
  100% {
    opacity: 1;
    transform: scale(1) rotate(0deg);
  }
  50% {
    opacity: 0.5;
    transform: scale(1.1) rotate(180deg);
  }
}

/* Title */
.title-gradient {
  font-size: 3rem;
  font-weight: bold;
  text-align: center;
  margin-bottom: 1.5rem;
  background: linear-gradient(135deg, #c9756f, #d4af87, #747f6e, #6b4654);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Divider */
.divider-container {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 2rem;
}

.divider-line {
  flex: 1;
  height: 2px;
  background: linear-gradient(to right, transparent, #c9756f, transparent);
}

.divider-dot {
  width: 8px;
  height: 8px;
  background: #c9756f;
  border-radius: 50%;
}

/* Main Paragraph */
.main-paragraph {
  font-size: 1.125rem;
  line-height: 1.9;
  color: #6b4654;
  text-align: center;
  margin-bottom: 2rem;
}

.main-paragraph strong {
  color: #c9756f;
  font-weight: 600;
}

/* Icon Tags */
.icon-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}

.icon-tag {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  border-radius: 9999px;
  font-size: 0.9rem;
  font-weight: 600;
  box-shadow: 0 4px 10px -2px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
}

.icon-tag:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 20px -5px rgba(0, 0, 0, 0.15);
}

.tag-1 {
  background: linear-gradient(135deg, rgba(201, 117, 111, 0.13), rgba(201, 117, 111, 0.07));
  color: #c9756f;
  border: 2px solid rgba(201, 117, 111, 0.27);
}

.tag-2 {
  background: linear-gradient(135deg, rgba(212, 175, 135, 0.13), rgba(212, 175, 135, 0.07));
  color: #d4af87;
  border: 2px solid rgba(212, 175, 135, 0.27);
}

.tag-3 {
  background: linear-gradient(135deg, rgba(116, 127, 110, 0.13), rgba(116, 127, 110, 0.07));
  color: #747f6e;
  border: 2px solid rgba(116, 127, 110, 0.27);
}

.tag-4 {
  background: linear-gradient(135deg, rgba(107, 70, 84, 0.13), rgba(107, 70, 84, 0.07));
  color: #6b4654;
  border: 2px solid rgba(107, 70, 84, 0.27);
}

/* Bottom Decoration */
.bottom-decoration {
  margin-top: 3rem;
  text-align: center;
}

.decoration-line {
  width: 100px;
  height: 4px;
  background: linear-gradient(to right, #c9756f, #d4af87, #747f6e);
  margin: 0 auto;
  border-radius: 9999px;
}

/* Responsive */
@media (max-width: 768px) {
  .content-card {
    padding: 2.5rem 2rem;
  }

  .title-gradient {
    font-size: 2rem;
  }

  .main-paragraph {
    font-size: 1rem;
  }

  .floating-icon {
    display: none;
  }

  .icon-tags {
    gap: 0.75rem;
  }

  .icon-tag {
    padding: 0.6rem 1.2rem;
    font-size: 0.85rem;
  }

  .shape {
    display: none;
  }
}

@media (max-width: 480px) {
  .content-card {
    padding: 2rem 1.5rem;
  }

  .title-gradient {
    font-size: 1.75rem;
  }

  .main-paragraph {
    font-size: 0.95rem;
    line-height: 1.7;
  }

  .corner-decoration {
    width: 30px;
    height: 30px;
  }
}
</style>
