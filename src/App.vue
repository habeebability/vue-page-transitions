<script setup>
import { ref } from "vue";

const anim = ref("fade");
</script>

<template>
  <div>
    <nav class="flex justify-center items-center p-6 space-x-5">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>

    <div class="check flex justify-center items-center">
      <label class="ml-2" for="fade">
        <input type="radio" name="anim" value="fade" v-model="anim" /> Fade
      </label>
      <label class="ml-2" for="slide">
        <input type="radio" name="anim" value="slide" v-model="anim" /> Slide
      </label>
      <label class="ml-2" for="slide-down">
        <input type="radio" name="anim" value="slide-down" v-model="anim" /> Slide Down
      </label>
      <label class="ml-2" for="grow-in">
        <input type="radio" name="anim" value="grow-in" v-model="anim" /> Grow in
      </label>
      <label class="ml-2" for="grow-out">
        <input type="radio" name="anim" value="grow-out" v-model="anim" /> Grow out
      </label>
    </div>
    <router-view v-slot="{ Component }">
      <transition :name="anim" mode="out-in">
        <Component :is="Component" />
      </transition>
    </router-view>
  </div>
</template>

<style >
nav a {
  color: black;
}
nav a:hover,
nav a.router-link-exact-active {
  color: crimson;
  text-decoration: underline;
}

/* transition name is fade */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease-in-out;
}

/* transition name is slide */
.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateX(-100%);
}

.slide-enter-active,
.slide-leave-active {
  transition: 0.5s ease-in-out;
}

/* transition name is slide-down */
.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(300px);
}

.slide-down-enter-active,
.slide-down-leave-active {
  transition: 0.5s ease-in-out;
}

/* transition name is grow in  */
.grow-in-enter-from,
.grow-in-leave-to {
  opacity: 0;
  transform: scale(0.2);
}

.grow-in-enter-active,
.grow-in-leave-active {
  transition: 0.5s ease-in-out;
}
/* transition name is grow out  */
.grow-out-enter-from,
.grow-out-leave-to {
  opacity: 0;
  transform: scale(1.2);
}

.grow-out-enter-active,
.grow-out-leave-active {
  transition: 0.5s ease-in-out;
}
</style>
