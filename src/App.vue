<template>
  <div id="app">
    <h1>VueX App</h1>
    <p>{{ user }}</p>

    <cc-users></cc-users>
  </div>
</template>

<script>
  import CcUsers from './components/users/main.vue'
  import { mapState, mapActions } from 'vuex'

  export default {
    name: 'vuex-app',

    mounted() {
      const payload = {
        name: 'Gustavo Cardoso',
        email: 'gustavocardoso@gmail.com',
        city: 'Bauru',
        state: 'SP',
        level: 'admin'
      }

      setTimeout(() => {
        this.changeUser(payload)
        // this.$store.dispatch('changeUser', payload)
      }, 1000)
    },

    components: {
      CcUsers
    },

    computed: {
      ...mapState({
        user: state => {
          const { name, email, level } = state.user
          return `${name} (${email}) is logged as ${level}.`
        }
      })
      // user() {
      //   const { name, email, level } = this.$store.state.user
      //   return `${name} (${email}) is logged as ${level}.`
      // }
    },

    methods: {
      ...mapActions(['changeUser'])
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

a {
  color: #42b983;
}

button {
  font-size: .8em;
  font-weight: bold;
  color: #fafafa;
  border-radius: 5px;
  border: 0;
  background: #41B883;
  padding: 1em;
}

button:disabled {
  background: #ccc;
}
</style>