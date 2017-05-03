<template>
  <div>
    <button v-on:click="changeUserData" v-bind:disabled="!hasUser">Change user data</button>
  </div>
</template>

<script>
  import { mapActions } from 'vuex'
  
  export default {
    methods: {
      changeUserData() {
        const payload = {
          name: 'Olívia Martins Faria',
          email: 'oliviamartinsfaria@gmail.com',
          city: 'São Paulo',
          state: 'SP',
          level: 'contributor'
        }

        this.changeUser(payload)
      },

      ...mapActions(['changeUser'])
    },

    computed: {
      hasUser() {
        return this.$store.state.user.name !== ''
      }
    }
  }
</script>