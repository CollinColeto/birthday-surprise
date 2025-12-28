<template>
  <section class="big-message">

    <!-- 🎁 Gift Box -->
    <div class="gift-wrapper" v-if="!opened" @click="openGift">
      <div class="gift-box">
        <div class="lid"></div>
        <div class="box"></div>
      </div>
      <span class="gift-text">Tap to open 🎁</span>
    </div>

    <!-- 📜 Scroll -->
    <transition name="scroll">
      <div class="scroll" v-if="opened">
        <p class="surprise">A little surprise just for you 💖</p>
        <a href="/BirthdaySurprise.zip" download="BirthdaySurprise.zip">
          Download your birthday surprise 🎉
        </a>
      </div>
    </transition>

    <h2>Another Year, Another Beautiful Chapter</h2>

    <p>
      This year is a blank page waiting for your story.
      Happy Birthday — today and always. 🎂✨
    </p>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const opened = ref(false)

const openGift = () => {
  opened.value = true
}
</script>

<style scoped>
.big-message {
  text-align: center;
  padding: 2rem;
}

/* 🎁 Gift Box */
.gift-wrapper {
  cursor: pointer;
  margin: 2rem 0;
}

.gift-box {
  position: relative;
  width: 100px;
  height: 80px;
  margin: auto;
}

.box {
  width: 100%;
  height: 60px;
  background: #e63946;
  border-radius: 0 0 8px 8px;
}

.lid {
  position: absolute;
  top: -20px;
  width: 100%;
  height: 30px;
  background: #f1a1a8;
  border-radius: 8px 8px 0 0;
  animation: lidOpen 0.8s forwards;
}

/* 📜 Scroll */
.scroll {
  background: #fff5e6;
  padding: 1.5rem;
  border-radius: 12px;
  width: 260px;
  margin: 1.5rem auto;
  box-shadow: 0 10px 30px rgba(0,0,0,0.15);
}

.scroll a {
  display: inline-block;
  margin-top: 0.8rem;
  color: #e63946;
  font-weight: bold;
  text-decoration: none;
}

/* Animations */
@keyframes lidOpen {
  to {
    transform: translateY(-25px) rotate(-15deg);
  }
}

.scroll-enter-active {
  animation: scrollOpen 0.6s ease-out;
}

@keyframes scrollOpen {
  from {
    transform: scaleY(0);
    opacity: 0;
  }
  to {
    transform: scaleY(1);
    opacity: 1;
  }
}

.gift-text {
  display: block;
  margin-top: 0.5rem;
  font-size: 0.9rem;
  color: #555;
}

.surprise {
  display: block;
  margin-top: 0.5rem;
  font-size: 0.9rem;
  color: #141414;
}
</style>
