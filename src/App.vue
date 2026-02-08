<script setup lang="ts">
import { ref } from 'vue'

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

// Smooth scrolling for anchor links
const scrollToSection = (id: string) => {
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
    isMenuOpen.value = false
  }
}

const sundaes = [
  { flavor: 'Caramel Sundae', price8: 45, price12: 75, image: '/ice-cream-menu.jpg' },
  { flavor: 'Chocolate Sundae', price8: 45, price12: 75, image: '/ice-cream-menu.jpg' },
  { flavor: 'Strawberry Sundae', price8: 45, price12: 75, image: '/ice-cream-menu.jpg' },
  { flavor: 'Ube Sundae', price8: 45, price12: 75, image: '/ice-cream-menu.jpg' },
  { flavor: 'Biscoff Sundae', price8: 60, price12: 90, image: '/ice-cream-menu.jpg' },
  { flavor: 'Oreo Sundae', price8: 50, price12: 80, image: '/ice-cream-menu.jpg' },
  { flavor: 'Mango Graham Sundae', price8: 60, price12: 90, image: '/ice-cream-menu.jpg' },
  { flavor: 'Rocky Road Sundae', price8: 55, price12: 85, image: '/ice-cream-menu.jpg' },
]

const fruitSodas = [
  { flavor: 'Blueberry Soda', price16: 45, price22: 65 },
  { flavor: 'Strawberry Soda', price16: 35, price22: 55 },
  { flavor: 'Green Apple Soda', price16: 35, price22: 55 },
  { flavor: 'Lychee Soda', price16: 35, price22: 55 },
  { flavor: 'Blue Lemonade Soda', price16: 35, price22: 55 },
  { flavor: 'Four Season Soda', price16: 35, price22: 55 },
]

const fluffyWaffles = [
  { item: 'Regular Fluffy Waffle', price: 30, isSinglePrice: true },
  { item: 'Chocolate Fluffy Waffle', half: 45, whole: 65 },
  { item: 'Strawberry Fluffy Waffle', half: 45, whole: 65 },
  { item: 'Caramel Fluffy Waffle', half: 45, whole: 65 },
  { item: 'Ube Fluffy Waffle', half: 45, whole: 65 },
  { item: 'Biscoff Fluffy Waffle', half: 85, whole: 140 },
  { item: 'Oreo Fluffy Waffle', half: 75, whole: 130 },
  { item: 'Mango Graham Fluffy Waffle', half: 85, whole: 140 },
  { item: 'Rocky Road Fluffy Waffle', half: 75, whole: 130 },
  { item: 'Tuna Sandwich Fluffy Waffle', half: 85, whole: 140 },
  { item: 'Nutella Banana Fluffy Waffle', half: 75, whole: 130 },
  { item: 'Ham & Cheese Fluffy Waffle', half: 80, whole: 135 },
]

const stickWaffles = [
  { item: 'Regular Stick Waffle', price: 20 },
  { item: 'Chocolate Stick Waffle', price: 30 },
  { item: 'Caramel Stick Waffle', price: 30 },
  { item: 'Strawberry Stick Waffle', price: 30 },
  { item: 'Ube Stick Waffle', price: 30 },
  { item: 'Hotdog Stick Waffle', price: 40 },
  { item: 'Mozzarella Stick Waffle', price: 40 },
  { item: 'Tuna Sandwich Stick Waffle', price: 45 },
]
</script>

<template>
  <header class="header">
    <div class="container header-container">
      <div class="logo">
        <img src="/logo.jpg" alt="Waffle Avenue Logo" class="logo-img" />
      </div>

      <button class="menu-toggle" @click="toggleMenu">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>

      <nav :class="['nav-menu', { active: isMenuOpen }]">
        <a @click="scrollToSection('hero')" class="nav-link">Home</a>
        <a @click="scrollToSection('ice-cream')" class="nav-link">Ice Cream</a>
        <a @click="scrollToSection('snacks')" class="nav-link">Snacks</a>
        <a @click="scrollToSection('contact')" class="nav-link">Contact</a>
      </nav>
    </div>
  </header>

  <main>
    <!-- Hero Section -->
    <section id="hero" class="hero">
      <div class="hero-decorative left">
        <img src="/waffle.png" alt="Delicious Waffle" />
      </div>
      <div class="hero-decorative right">
        <img src="/waffle2.png" alt="Tasty Waffle" />
      </div>
      <div class="container hero-content">
        <h1>Waffle Avenue</h1>
        <p class="tagline">Share the Waffle, Share the Moment</p>
        <div class="cta-group">
          <button @click="scrollToSection('ice-cream')" class="btn btn-primary">View Menu</button>
        </div>
      </div>
    </section>

    <!-- Ice Cream Menu Section -->
    <section id="ice-cream" class="section bg-light">
      <div class="container">
        <h2 class="section-title">Ice Cream Menu</h2>

        <!-- Sundaes -->
        <h3 class="category-title">Sundaes</h3>
        <div class="grid grid-4">
          <div v-for="(item, index) in sundaes" :key="index" class="menu-card">
            <div class="price-badge">
              <span>8oz ₱{{ item.price8 }}</span>
              <span>12oz ₱{{ item.price12 }}</span>
            </div>
            <h4>{{ item.flavor }}</h4>
          </div>
        </div>

        <!-- Cones and Floats -->
        <div class="grid grid-2 mt-5">
          <!-- Cones -->
          <div class="highlight-card">
            <h3>Cones</h3>
            <ul class="menu-list">
              <li>
                <div class="menu-item-header">
                  <span class="item-name">Dolce Waffle Cone</span>
                  <span class="item-price">₱20</span>
                </div>
                <p class="item-desc">Chocolate, Vanilla & Mixed Ice Cream</p>
              </li>
              <li>
                <div class="menu-item-header">
                  <span class="item-name">Giant Waffle Cone</span>
                  <span class="item-price">₱35</span>
                </div>
                <p class="item-desc">Chocolate, Vanilla & Mixed Ice Cream</p>
              </li>
            </ul>
          </div>

          <!-- Floats -->
          <div class="highlight-card">
            <h3>Floats</h3>
            <ul class="menu-list">
              <li>
                <div class="menu-item-header">
                  <span class="item-name">Choco Float</span>
                </div>
                <div class="item-prices"><span>16oz ₱70</span> | <span>22oz ₱100</span></div>
              </li>
              <li>
                <div class="menu-item-header">
                  <span class="item-name">Coke Float</span>
                </div>
                <div class="item-prices"><span>16oz ₱50</span> | <span>22oz ₱80</span></div>
              </li>
            </ul>
          </div>
        </div>

        <!-- Fruit Soda -->
        <h3 class="category-title mt-5">Fruit Soda</h3>
        <div class="upgrade-banner">Upgrade your fruit soda to a soda float for only + ₱10!</div>
        <div class="grid grid-3">
          <div v-for="(item, index) in fruitSodas" :key="index" class="simple-card">
            <h4>{{ item.flavor }}</h4>
            <div class="prices">
              <span>16oz ₱{{ item.price16 }}</span>
              <span>22oz ₱{{ item.price22 }}</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Snacks Menu Section -->
    <section id="snacks" class="section">
      <div class="container">
        <h2 class="section-title">Snacks Menu</h2>

        <!-- Fluffy Waffles -->
        <h3 class="category-title">Fluffy Waffles</h3>
        <div class="grid grid-3">
          <div v-for="(item, index) in fluffyWaffles" :key="index" class="waffle-card">
            <h4>{{ item.item }}</h4>
            <div class="d-flex justify-between">
              <span v-if="item.isSinglePrice" class="single-price">₱{{ item.price }}</span>
              <template v-else>
                <span class="price-tag">Half ₱{{ item.half }}</span>
                <span class="price-tag">Whole ₱{{ item.whole }}</span>
              </template>
            </div>
          </div>
        </div>

        <!-- Stick Waffles -->
        <h3 class="category-title mt-5">Stick Waffles</h3>
        <div class="grid grid-4">
          <div v-for="(item, index) in stickWaffles" :key="index" class="stick-card">
            <h4>{{ item.item }}</h4>
            <span class="price-pill">₱{{ item.price }}</span>
          </div>
        </div>

        <!-- Fries, Siomai & Snacks -->
        <div class="others-section mt-5">
          <h3 class="category-title">Fries, Siomai & Snacks</h3>
          <div class="grid grid-3">
            <div class="snack-column">
              <h4>Fries</h4>
              <ul class="snack-list">
                <li><strong>Barkada Fries</strong> (Choose 3) - ₱180</li>
                <li><strong>BFF Fries</strong> (Choose 2) - ₱105</li>
                <li><strong>Large Fries</strong> (Choose 1) - ₱65</li>
              </ul>
              <p class="flavors">Flavors: Sour Cream, Cheese, BBQ, Spicy BBQ</p>
            </div>
            <div class="snack-column">
              <h4>Siomai</h4>
              <ul class="snack-list">
                <li><strong>Premium Siomai</strong> - ₱35</li>
                <li>Beef Siomai, Pork Siomai</li>
              </ul>
            </div>
            <div class="snack-column">
              <h4>Snacks on a Cup</h4>
              <p class="price-large">₱30</p>
              <p class="note">Choose 1 Soda drink just add</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section bg-primary text-white">
      <div class="container text-center">
        <h2>Visit Us Today!</h2>
        <p class="mb-4">Come satisfy your cravings at Waffle Avenue.</p>
        <div class="social-links">
          <!-- Social placeholders -->
          <span>See us on Facebook and Instagram</span>
        </div>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div class="container text-center">
      <p>
        &copy; {{ new Date().getFullYear() }} Waffle Avenue. Share the waffle, share the moment.
      </p>
    </div>
  </footer>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  z-index: 1000;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  height: var(--header-height);
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100%;
}

.logo-img {
  height: 50px;
  width: auto;
}

.nav-menu {
  display: flex;
  gap: 30px;
}

.nav-link {
  font-weight: 600;
  font-family: var(--font-heading);
  color: var(--primary);
  cursor: pointer;
}

.nav-link:hover {
  color: var(--accent);
}

.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
}

.bar {
  width: 25px;
  height: 3px;
  background-color: var(--primary);
  transition: 0.3s;
}

.hero {
  position: relative;
  height: 100vh;
  min-height: 700px;
  background-color: #f7d794; /* Waffle base color */
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.3) 2px, transparent 2px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.3) 2px, transparent 2px),
    linear-gradient(rgba(184, 134, 11, 0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(184, 134, 11, 0.1) 1px, transparent 1px);
  background-size:
    60px 60px,
    60px 60px,
    15px 15px,
    15px 15px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 0;
  overflow: hidden;
}

.hero-decorative {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 400px;
  max-width: 35vw;
  z-index: 1;
  /* Removed opacity */
  transition: transform 0.3s ease;
  animation: float 6s ease-in-out infinite;
}

.hero-decorative img {
  width: 100%;
  height: auto;
  /* Replaced box-shadow with drop-shadow for cleaner look on PNGs */
  filter: drop-shadow(0 15px 25px rgba(0, 0, 0, 0.3));
  border-radius: 0; /* Let PNG shape dictate */
}

.hero-decorative.left {
  left: -20px;
  transform: translateY(-50%) rotate(-5deg);
}

.hero-decorative.right {
  right: -20px;
  transform: translateY(-50%) rotate(5deg);
  animation-delay: -3s; /* Offset animation */
}

@keyframes float {
  0% {
    transform: translateY(-50%) rotate(-5deg);
  }
  50% {
    transform: translateY(-55%) rotate(-2deg);
  }
  100% {
    transform: translateY(-50%) rotate(-5deg);
  }
}

@keyframes float-right {
  0% {
    transform: translateY(-50%) rotate(5deg);
  }
  50% {
    transform: translateY(-45%) rotate(8deg);
  }
  100% {
    transform: translateY(-50%) rotate(5deg);
  }
}

.hero-decorative.left {
  animation-name: float;
}
.hero-decorative.right {
  animation-name: float-right;
}

.hero:hover .hero-decorative.left {
  transform: translateY(-50%) scale(1.05);
}

.hero:hover .hero-decorative.right {
  transform: translateY(-50%) scale(1.05);
}

.hero-overlay {
  display: none;
}

.hero-content {
  position: relative;
  z-index: 2;
  text-align: center;
  background: rgba(255, 255, 255, 0.95);
  padding: 3rem 4rem;
  border-radius: 30px;
  box-shadow:
    0 20px 60px rgba(0, 0, 0, 0.1),
    0 0 0 8px rgba(255, 255, 255, 0.5);
  border: 2px solid var(--accent);
  max-width: 800px;
  margin: 0 20px;
}

.hero h1 {
  font-size: 4.5rem;
  color: var(--primary);
  text-transform: uppercase;
  text-shadow: 2px 2px 0px var(--accent);
  margin-bottom: 0.2em;
  letter-spacing: 2px;
}

.tagline {
  font-size: 1.5rem;
  font-weight: 500; /* Increased weight */
  margin-bottom: 2rem;
  font-style: italic;
  color: var(--primary-light);
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 3rem;
  position: relative;
  display: inline-block;
  width: 100%;
}

.section-title::after {
  content: '';
  display: block;
  width: 60px;
  height: 4px;
  background: var(--accent);
  margin: 10px auto 0;
  border-radius: 2px;
}

.category-title {
  font-size: 1.8rem;
  margin: 2rem 0 1.5rem;
  color: var(--primary-light);
  border-left: 5px solid var(--accent);
  padding-left: 15px;
}

.bg-light {
  background-color: var(--secondary);
}

.bg-primary {
  background-color: var(--primary);
}

.mb-4 {
  margin-bottom: 2rem;
}
.mt-5 {
  margin-top: 3rem;
}

/* Cards */
.menu-card {
  background: var(--white);
  padding: 20px;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  transition: 0.3s;
  border: 1px solid var(--gray-200);
}

.menu-card:hover {
  transform: translateY(-5px);
  border-color: var(--accent);
}

.price-badge {
  display: flex;
  flex-direction: column;
  gap: 5px;
  margin-bottom: 10px;
  font-weight: bold;
  color: var(--accent);
}

.highlight-card {
  background: var(--white);
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);
}

.menu-list {
  list-style: none;
}

.menu-list li {
  margin-bottom: 1.5rem;
  border-bottom: 1px dashed var(--gray-200);
  padding-bottom: 1rem;
}

.menu-item-header {
  display: flex;
  justify-content: space-between;
  font-weight: 700;
  font-size: 1.1rem;
}

.item-price {
  color: var(--primary);
}

.upgrade-banner {
  background: linear-gradient(135deg, var(--accent), #ffca28);
  color: var(--primary);
  padding: 15px;
  border-radius: 10px;
  text-align: center;
  font-weight: bold;
  font-size: 1.1rem;
  margin-bottom: 2rem;
}

.simple-card {
  background: var(--white);
  padding: 15px;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.prices {
  display: flex;
  flex-direction: column;
  text-align: right;
  font-size: 0.9rem;
  color: var(--text-dark);
}

.waffle-card {
  background: var(--white);
  padding: 20px;
  border-radius: 12px;
  border-left: 4px solid var(--primary);
}

.d-flex {
  display: flex;
}
.justify-between {
  justify-content: space-between;
}

.price-tag {
  background: var(--secondary);
  padding: 4px 8px;
  border-radius: 4px;
  font-size: 0.85rem;
  color: var(--primary);
  margin-left: 5px;
}

.stick-card {
  background: var(--white);
  padding: 15px;
  border-radius: 30px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 2px solid var(--gray-100);
}

.price-pill {
  background: var(--primary);
  color: var(--white);
  padding: 5px 12px;
  border-radius: 20px;
  font-weight: bold;
}

.snack-column {
  background: var(--gray-100);
  padding: 20px;
  border-radius: 15px;
}

.snack-list li {
  margin-bottom: 8px;
}

.flavors {
  font-style: italic;
  font-size: 0.9rem;
  color: #666;
  margin-top: 10px;
}

.price-large {
  font-size: 3rem;
  font-weight: bold;
  color: var(--primary);
  margin: 10px 0;
}

.footer {
  background-color: #0d3332;
  color: rgba(255, 255, 255, 0.7);
  padding: 40px 0;
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .menu-toggle {
    display: flex;
  }

  .nav-menu {
    position: fixed;
    top: var(--header-height);
    left: 0;
    width: 100%;
    background: var(--white);
    flex-direction: column;
    padding: 20px;
    gap: 15px;
    transform: translateY(-150%);
    transition: transform 0.3s ease;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
  }

  .nav-menu.active {
    transform: translateY(0);
  }

  .hero h1 {
    font-size: 2.5rem;
  }

  .hero-content {
    padding: 2rem;
  }
}
</style>
