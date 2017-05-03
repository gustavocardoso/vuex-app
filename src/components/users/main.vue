<template>
  <div>
    <p>Localidade: {{ localidade }}</p>
    <p>E-mail: {{ email }}</p>
    <cc-button></cc-button>
  </div>
</template>

<script>
  import CcButton from '../button.vue'

  export default {
    components: {
      CcButton
    },

    computed: {
      email() {
        return this.$store.state.user.email
      },

      localidade() {
        return this.$store.getters.localidade
      }
    }
  }
</script>