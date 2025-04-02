<template>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container">
        <router-link class="navbar-brand" to="/">Sistema de Asistencia</router-link>
        
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav">
          <span class="navbar-toggler-icon"></span>
        </button>
        
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ml-auto">
            <template v-if="isAuthenticated">
              <li class="nav-item">
                <router-link class="nav-link" to="/dashboard">Dashboard</router-link>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/mark-attendance">Marcar Asistencia</router-link>
              </li>
              <li class="nav-item">
                <router-link class="nav-link" to="/generate-code">Generar Código</router-link>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#" @click.prevent="logout">Cerrar Sesión</a>
              </li>
            </template>
            <template v-else>
              <li class="nav-item">
                <router-link class="nav-link" to="/login">Iniciar Sesión</router-link>
              </li>
            </template>
          </ul>
        </div>
      </div>
    </nav>
  </template>
  
  <script>
  export default {
    name: 'NavBar',
    computed: {
      isAuthenticated() {
        return this.$store.getters.isAuthenticated
      }
    },
    methods: {
      logout() {
        this.$store.dispatch('logout')
        this.$router.push('/login')
      }
    }
  }
  </script>