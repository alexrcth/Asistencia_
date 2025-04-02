<template>
  <div class="auth-container">
    <div class="auth-form">
      <h2>Iniciar Sesión</h2>
      <div v-if="error" class="alert alert-danger">{{ error }}</div>
      <form @submit.prevent="handleSubmit">
        <div class="form-group">
          <label>Usuario</label>
          <input
            type="text"
            class="form-control"
            v-model="username"
            required
          />
        </div>
        <div class="form-group">
          <label>Contraseña</label>
          <input
            type="password"
            class="form-control"
            v-model="password"
            required
          />
        </div>
        <button type="submit" class="btn btn-primary" :disabled="loading">
          {{ loading ? 'Procesando...' : 'Ingresar' }}
        </button>
      </form>
    </div>
  </div>
</template>

<script>
import AuthService from '@/services/auth.service';

export default {
  name: 'LoginForm',
  data() {
    return {
      username: '',
      password: '',
      error: '',
      loading: false
    };
  },
  methods: {
    async handleSubmit() {
      this.loading = true;
      this.error = '';
      
      if (!this.username || !this.password) {
        this.error = 'Por favor ingrese usuario y contraseña';
        this.loading = false;
        return;
      }
      
      const success = await AuthService.login(this.username, this.password);
      if (success) {
        this.$router.push('/dashboard');
      } else {
        this.error = 'Usuario o contraseña incorrectos';
      }
      this.loading = false;
    }
  }
};
</script>

<style scoped>
.auth-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 70vh;
}

.auth-form {
  width: 100%;
  max-width: 400px;
  padding: 20px;
  background-color: #f8f9fa;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

.form-control {
  width: 100%;
  padding: 8px;
  font-size: 16px;
  border: 1px solid #ced4da;
  border-radius: 4px;
}

.btn {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  margin-top: 10px;
}
</style>