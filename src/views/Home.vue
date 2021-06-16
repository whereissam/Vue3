<template>
  <div class="home">
    <!-- <transition name="toast"> -->
      <Toast v-if="showToast" />
    <!-- </transition> -->
    <Todos @badValue="triggerToast" />
    <transition name="fade">
      <div v-if="showP">Hello, sam</div>
    </transition>

    <button @click="showP = !showP">toggle</button>
  </div>
</template>

<script>
import { ref } from 'vue'
import Toast from '../components/Toast'
import Todos from '../components/Todos'

export default {
  components: { Toast, Todos },
  setup() {
    const showToast = ref(false)
    const showP = ref(false)

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => showToast.value = false, 3000)
    }

    return { showToast, triggerToast, showP }
  }
}
</script>

<style>

  .fade-enter-from{
    opacity: 0;
  }
  /* .fade-enter-to{
    opacity: 1;
  } */
  .fade-enter-active,
  .fade-leave-active{
    animation: wobble 4s ease;
  }
  /* .fade-leave-from{
    opacity: 1; */
  /* } */
  .fade-leave-to{
    opacity: 0;
  }
  

  /* enter transitions */
  /* .toast-enter-active {
    animation: wobble 0.5s ease;
  } */
  /* leave transitions */
  /* .toast-leave-to {
    opacity: 0;
    transform: translateY(-60px);
  }
  .toast-leave-active {
    transition: all 0.3s ease;
  } */

  @keyframes wobble {
    0% { transform: translateY(-100px); opacity: 0 }
    50% { transform: translateY(0px); opacity: 1 }
    60% { transform: translateX(8px); opacity: 1 }
    70% { transform: translateX(-8px); opacity: 1 }
    80% { transform: translateX(4px); opacity: 1 }
    90% { transform: translateX(-4px); opacity: 1 }
    100% { transform: translateX(0px); opacity: 1 }
  }
</style>