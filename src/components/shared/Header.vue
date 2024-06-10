<template>
    <header 
      class='header'
    >
       <div class="container header__inner">
        <div class="header__left">
            <Logo />
            <nav class="nav">
                <ul>
                    <li>
                        <a href="/rates">Тарифы</a>
                    </li>
                    <li>
                        <a href="/contacts">Контакты</a>
                    </li>
                </ul>
            </nav>
        </div> 
        <div class="header__right">
            <div class="phone">
                <a href="tel:+74951184422"> +7 495 118-44-22</a>
            </div>
            <Button :variant="'transparent'">
                <NuxtLink to="/signin">Вход</NuxtLink>
            </Button>
            <Button :variant="'primary'">
                <NuxtLink to="/signup">Регистрация</NuxtLink>
            </Button>
        </div> 
        <div class="menu-btn" @click.stop="toggleMenu">
            <img v-if="isMenuOpen" src="~/assets/images/close.svg" alt="menu-icon">
            <img v-else src="~/assets/images/menu.svg" alt="menu-icon">
        </div>
       </div>
       <transition name="fade">
            <div v-if="isMenuOpen" class="menu">
                <ul class="menu-links">
                    <li>
                        <a href="/rates">Тарифы</a>
                    </li>
                    <li>
                        <a href="/contacts">Контакты</a>
                    </li>
                </ul>
                <div class="phone">
                    <a href="tel:+74951184422"> +7 495 118-44-22</a>
                </div>
                <Button :variant="'transparent'">
                    <NuxtLink to="/signin">Вход</NuxtLink>
                </Button>
                <Button :variant="'primary'">
                    <NuxtLink to="/signup">Регистрация</NuxtLink>
                </Button>
            </div>
        </transition>
    </header>
</template>

<script setup lang="ts">
import Logo from './Logo.vue';
import Button from '../ui/Button.vue'
import { useRouter } from 'vue-router'

import { ref, onBeforeMount } from 'vue'

const router = useRouter()
const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const handleClickOutside = (event) => {
  if (!event.target.closest('.menu')) {
    isMenuOpen.value = false
  }
}

onBeforeMount(() => {
  document.addEventListener('click', handleClickOutside)
})

onBeforeUnmount(() => {
  document.removeEventListener('click', handleClickOutside)
})

router.beforeEach((to, from, next) => {
  if (isMenuOpen.value) {
    isMenuOpen.value = false
  }
  next()
})

</script>
