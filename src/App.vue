<script setup lang="ts">
import Navbar from './components/Navbar.vue'
</script>

<template>
  <div class="page">
    <Navbar />

    <header class="hero">
      <div class="hero-copy">
        <p class="eyebrow">Welcome to</p>
        <h1>ENET Website</h1>
        <p class="description">
          A clean, modern landing page with a floating navigation bar.
        </p>
        <a class="cta" href="#contact">Get Started</a>
      </div>

      <div class="hero-panels">
        <div class="hero-side-card">
          <h3>Fast Launch</h3>
          <p>
            เตรียมเว็บไซต์ให้พร้อมใช้งานเร็วภายในเวลาสั้น.
          </p>
        </div>

        <div class="hero-side-card hero-secondary">
          <h3>Services</h3>
          <ul>
            <li>Landing page design</li>
            <li>Responsive layout</li>
          </ul>
        </div>
      </div>
    </header>

    <main class="content">
      <section id="about" class="card">
        <h2>About</h2>
        <p>สร้างเว็บไซต์ที่ใช้งานได้จริงและดูเป็นมืออาชีพ.</p>
      </section>

      <section id="contact" class="card">
        <h2>Contact</h2>
        <p>ติดต่อเราเพื่อเริ่มพัฒนาต้นแบบเว็บไซต์ที่สวยงามและใช้งานง่าย.</p>
      </section>
    </main>
  </div>
</template>

<style src="./App.css" scoped></style>