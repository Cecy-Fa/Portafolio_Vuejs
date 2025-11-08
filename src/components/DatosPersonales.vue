<script setup>
import { ref } from 'vue'
import {
  Linkedin,
  Instagram,
  Github,
  FileText,
  Phone,
  MapPin,
  Mail,
  Download,
  ArrowRight,
} from 'lucide-vue-next'

const hoveredSocial = ref(null)

const socialLinks = [
  { id: 'linkedin', iconComponent: Linkedin, color: '#0077B5', url: 'https://linkedin.com' },
  { id: 'instagram', iconComponent: Instagram, color: '#E4405F', url: 'https://instagram.com' },
  { id: 'github', iconComponent: Github, color: '#6B4654', url: 'https://github.com' },
  { id: 'cv', iconComponent: FileText, color: '#D4AF87', url: '#' },
]
</script>

<template>
  <div class="hero-section">
    <!-- Decorative Background -->
    <div class="hero-background">
      <div class="gradient-orb orb-1"></div>
      <div class="gradient-orb orb-2"></div>
      <div class="gradient-orb orb-3"></div>
      <div class="particles">
        <div v-for="i in 20" :key="i" :class="`particle particle-${i % 5}`"></div>
      </div>
    </div>

    <!-- Hero Content -->
    <div class="hero-content">
      <div class="content-grid">
        <!-- Left Side - Profile Image -->
        <div class="profile-section">
          <div class="profile-card">
            <div class="profile-image-wrapper">
              <div class="profile-ring ring-1"></div>
              <div class="profile-ring ring-2"></div>
              <div class="profile-ring ring-3"></div>
              <div class="profile-image">
                <div class="avatar-placeholder">
                  <span class="avatar-initials">FC</span>
                </div>
              </div>
            </div>
            <div class="status-badge">
              <div class="status-dot"></div>
            </div>
          </div>
        </div>

        <!-- Right Side - Info -->
        <div class="info-section">
          <div class="greeting-badge">
            <span class="wave">👋</span>
            <span>Hola, Bienvenido</span>
          </div>

          <h1 class="hero-title">
            <span class="title-line">Farias A. Cecilia</span>
          </h1>

          <div class="subtitle-container">
            <div class="subtitle-icon">🎓</div>
            <p class="hero-subtitle">Técnico Universitario en Programación - UTN</p>
          </div>

          <p class="hero-description">
            Soy un desarrollador web con experiencia en el desarrollo de aplicaciones web y móviles,
            especializado en crear soluciones digitales innovadoras y funcionales.
          </p>

          <!-- Contact Info -->
          <div class="contact-info">
            <div class="contact-item">
              <div
                class="contact-icon"
                style="background: linear-gradient(135deg, #c9756f, #db9690)"
              >
                <component :is="Phone" :size="16" />
              </div>
              <div class="contact-text">
                <span class="contact-label">Teléfono</span>
                <span class="contact-value">+549 2622-605090</span>
              </div>
            </div>
            <div class="contact-item">
              <div
                class="contact-icon"
                style="background: linear-gradient(135deg, #d4af87, #e6c9a8)"
              >
                <component :is="MapPin" :size="16" />
              </div>
              <div class="contact-text">
                <span class="contact-label">Ubicación</span>
                <span class="contact-value">Tupungato, Mendoza, AR</span>
              </div>
            </div>
          </div>

          <!-- Social Links -->
          <div class="social-links">
            <a
              v-for="social in socialLinks"
              :key="social.id"
              :href="social.url"
              target="_blank"
              class="social-link"
              @mouseenter="hoveredSocial = social.id"
              @mouseleave="hoveredSocial = null"
              :style="{ '--social-color': social.color }"
            >
              <component :is="social.iconComponent" :size="20" />
              <span v-if="hoveredSocial === social.id" class="social-tooltip">
                {{ social.id }}
              </span>
            </a>
          </div>
          <!-- CTA Buttons -->
          <div class="cta-buttons">
            <button class="btn-primary-hero">
              <component :is="Download" :size="18" />
              Descargar CV
              <component :is="ArrowRight" :size="18" class="btn-arrow" />
            </button>
            <button class="btn-secondary-hero">
              <component :is="Mail" :size="18" />
              Contáctame
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div class="scroll-indicator">
      <div class="scroll-mouse">
        <div class="scroll-wheel"></div>
      </div>
      <span class="scroll-text">Desliza para explorar</span>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-size: 2.5rem;
}

p {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.card {
  background-color: #f5f1ed; /*Etiqueta para cambiar el fondo del texto de la pantalla principal (Beig claro/ Crema)*/
  border-radius: 10px;
  padding: 10px;
  margin: 10px;
  text-align: center;
}

.container-lista {
  display: flex;
  justify-content: center;
  list-style: none;
  padding: 0;
  margin: 0;
  text-align: center;
}

.icon-redsocial {
  align-items: center;
  background-color: aliceblue;
  border-radius: 50%;
  padding: 2px;
  margin: 5px;
  box-shadow: 0 0 5px rgba(95, 124, 205, 0.934);
}

.icon-redsocial:hover {
  background-color: rgb(28, 41, 52);
  box-shadow: 0 0 5px rgba(251, 249, 249, 0.934);
}

h3 {
  font-size: 1.2rem;
  font-weight: 600;
}
/* ========================================
  ESTILOS PARA SECCIÓN INICIO
   ======================================== */

.hero-section {
  min-height: 100vh;
  background: #f5f1ed;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

/* Background */
.hero-background {
  position: absolute;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
}

.gradient-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.15;
  animation: float-smooth 20s ease-in-out infinite;
}

.orb-1 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, #c9756f 0%, transparent 70%);
  top: -200px;
  right: -100px;
}

.orb-2 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, #d4af87 0%, transparent 70%);
  bottom: -150px;
  left: -100px;
  animation-delay: 5s;
}

.orb-3 {
  width: 350px;
  height: 350px;
  background: radial-gradient(circle, #747f6e 0%, transparent 70%);
  top: 40%;
  left: 50%;
  animation-delay: 10s;
}

@keyframes float-smooth {
  0%,
  100% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(30px, -30px);
  }
}

/* Particles */
.particles {
  position: absolute;
  inset: 0;
}

.particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #c9756f;
  border-radius: 50%;
  opacity: 0.3;
  animation: particle-float 15s ease-in-out infinite;
}

.particle-0 {
  top: 20%;
  left: 10%;
  animation-delay: 0s;
  background: #c9756f;
}
.particle-1 {
  top: 40%;
  left: 30%;
  animation-delay: 2s;
  background: #d4af87;
}
.particle-2 {
  top: 60%;
  left: 50%;
  animation-delay: 4s;
  background: #747f6e;
}
.particle-3 {
  top: 30%;
  left: 70%;
  animation-delay: 6s;
  background: #6b4654;
}
.particle-4 {
  top: 80%;
  left: 20%;
  animation-delay: 8s;
  background: #c9756f;
}

@keyframes particle-float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-50px);
  }
}

/* Hero Content */
.hero-content {
  flex: 1;
  display: flex;
  align-items: center;
  padding: 2rem;
  position: relative;
  z-index: 10;
}

.content-grid {
  max-width: 1400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 4rem;
  align-items: center;
  width: 100%;
}

/* Profile Section */
.profile-section {
  display: flex;
  justify-content: center;
}

.profile-card {
  position: relative;
}

.profile-image-wrapper {
  position: relative;
  width: 320px;
  height: 320px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.profile-ring {
  position: absolute;
  border-radius: 50%;
  border: 2px solid;
  animation: rotate-ring 20s linear infinite;
}

.ring-1 {
  width: 100%;
  height: 100%;
  border-color: rgba(201, 117, 111, 0.3);
}

.ring-2 {
  width: 85%;
  height: 85%;
  border-color: rgba(212, 175, 135, 0.3);
  animation-duration: 15s;
  animation-direction: reverse;
}

.ring-3 {
  width: 70%;
  height: 70%;
  border-color: rgba(116, 127, 110, 0.3);
  animation-duration: 10s;
}

@keyframes rotate-ring {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.profile-image {
  width: 240px;
  height: 240px;
  border-radius: 50%;
  background: white;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 10;
}

.avatar-placeholder {
  width: 220px;
  height: 220px;
  border-radius: 50%;
  background: linear-gradient(135deg, #c9756f, #d4af87);
  display: flex;
  align-items: center;
  justify-content: center;
}

.avatar-initials {
  font-size: 4rem;
  font-weight: bold;
  color: white;
}

.status-badge {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  background: white;
  padding: 0.5rem 1.25rem;
  border-radius: 9999px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.85rem;
  font-weight: 600;
  color: #6b4654;
}

.status-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #4ade80;
  animation: pulse-dot 2s infinite;
}

@keyframes pulse-dot {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

/* Info Section */
.info-section {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.greeting-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: linear-gradient(135deg, rgba(201, 117, 111, 0.1), rgba(212, 175, 135, 0.1));
  padding: 0.5rem 1rem;
  border-radius: 9999px;
  width: fit-content;
  font-weight: 600;
  color: #6b4654;
  font-size: 0.95rem;
  border: 2px solid rgba(201, 117, 111, 0.2);
}

.wave {
  font-size: 1.25rem;
  animation: wave 2s ease-in-out infinite;
}

@keyframes wave {
  0%,
  100% {
    transform: rotate(0deg);
  }
  25% {
    transform: rotate(20deg);
  }
  75% {
    transform: rotate(-20deg);
  }
}

.hero-title {
  font-size: 4rem;
  font-weight: 800;
  line-height: 1.1;
  color: #6b4654;
  margin: 0;
}

.title-line {
  display: block;
}

.title-highlight {
  display: block;
  background: linear-gradient(135deg, #c9756f, #d4af87, #747f6e);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.subtitle-container {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.subtitle-icon {
  font-size: 1.5rem;
}

.hero-subtitle {
  font-size: 1.25rem;
  font-weight: 600;
  color: #8b8680;
  margin: 0;
}

.hero-description {
  font-size: 1.1rem;
  line-height: 1.7;
  color: #8b8680;
  max-width: 600px;
}

/* Contact Info */
.contact-info {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.contact-icon {
  width: 40px;
  height: 40px;
  border-radius: 0.75rem;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.contact-text {
  display: flex;
  flex-direction: column;
}

.contact-label {
  font-size: 0.75rem;
  color: #8b8680;
  font-weight: 500;
}

.contact-value {
  font-size: 0.95rem;
  color: #6b4654;
  font-weight: 600;
}

/* Social Links */
.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  position: relative;
  width: 50px;
  height: 50px;
  border-radius: 0.75rem;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #6b4654;
  text-decoration: none;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
}

.social-link:hover {
  background: var(--social-color);
  color: white;
  transform: translateY(-4px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
}

.social-tooltip {
  position: absolute;
  bottom: -35px;
  background: #6b4654;
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 0.5rem;
  font-size: 0.75rem;
  white-space: nowrap;
  text-transform: capitalize;
}

/* CTA Buttons */
.cta-buttons {
  display: flex;
  gap: 1rem;
  margin-top: 1rem;
}

.btn-primary-hero {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem 2rem;
  background: linear-gradient(135deg, #c9756f, #6b4654);
  color: white;
  border: none;
  border-radius: 0.75rem;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  box-shadow: 0 10px 30px rgba(201, 117, 111, 0.3);
  transition: all 0.3s ease;
}

.btn-primary-hero:hover {
  transform: translateY(-2px);
  box-shadow: 0 15px 40px rgba(201, 117, 111, 0.4);
}

.btn-arrow {
  transition: transform 0.3s ease;
}

.btn-primary-hero:hover .btn-arrow {
  transform: translateX(4px);
}

.btn-secondary-hero {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem 2rem;
  background: white;
  color: #6b4654;
  border: 2px solid #c9756f;
  border-radius: 0.75rem;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-secondary-hero:hover {
  background: #c9756f;
  color: white;
  transform: translateY(-2px);
}

/* Scroll Indicator */
.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  z-index: 10;
}

.scroll-mouse {
  width: 24px;
  height: 36px;
  border: 2px solid #c9756f;
  border-radius: 12px;
  display: flex;
  justify-content: center;
  padding-top: 6px;
}

.scroll-wheel {
  width: 3px;
  height: 8px;
  background: #c9756f;
  border-radius: 2px;
  animation: scroll-down 2s ease-in-out infinite;
}

@keyframes scroll-down {
  0%,
  100% {
    transform: translateY(0);
    opacity: 1;
  }
  50% {
    transform: translateY(8px);
    opacity: 0;
  }
}

.scroll-text {
  font-size: 0.75rem;
  color: #8b8680;
  font-weight: 500;
}

/* Responsive - Tablet */
@media (max-width: 1024px) {
  .content-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .profile-section {
    order: 2;
  }

  .info-section {
    order: 1;
    text-align: center;
    align-items: center;
  }

  .hero-title {
    font-size: 3rem;
  }

  .cta-buttons {
    justify-content: center;
  }

  .contact-info {
    justify-content: center;
  }

  .social-links {
    justify-content: center;
  }
}

/* Responsive - Mobile */
@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }

  .profile-image-wrapper {
    width: 260px;
    height: 260px;
  }

  .profile-image {
    width: 200px;
    height: 200px;
  }

  .avatar-placeholder {
    width: 180px;
    height: 180px;
  }

  .avatar-initials {
    font-size: 3rem;
  }

  .contact-info {
    flex-direction: column;
    gap: 1rem;
  }

  .cta-buttons {
    flex-direction: column;
    width: 100%;
  }

  .btn-primary-hero,
  .btn-secondary-hero {
    width: 100%;
    justify-content: center;
  }

  .hero-subtitle {
    font-size: 1.1rem;
  }

  .hero-description {
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 2rem;
  }

  .nav-container {
    padding: 0.5rem 1rem;
  }

  .logo-text {
    display: none;
  }
}
</style>
