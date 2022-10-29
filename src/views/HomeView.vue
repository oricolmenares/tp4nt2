<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <formulario-vue />
  </div>
</template>

<script>
// @ is an alias to /src
import FormularioVue from '@/components/FormularioVue.vue'

export default {
  name: 'HomeView',
  components: {
    FormularioVue
  }
}
</script>
