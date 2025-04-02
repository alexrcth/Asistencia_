<template>
  <div class="login-container">
    <div class="rotating-wheel"></div>
    <div class="login-box">
      <h2>Login</h2>
      <form>
        <div class="input-container">
          <input type="email" placeholder="Email" required />
        </div>
        <div class="input-container">
          <input type="password" placeholder="Password" required />
        </div>
        <div class="forgot-password">Forgot Password?</div>
        <button type="submit">Login</button>
        <div class="signup">Signup</div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.login-container {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #0b1728;
}

.rotating-wheel {
  position: absolute;
  width: 500px; /* Aumenta el tamaño */
  height: 500px; 
  border-radius: 50%;
  border: 10px solid transparent;
  border-top: 10px solid #00d9ff;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.login-box {
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  background: transparent;
  padding: 20px;
}

h2 {
  color: #00d9ff;
  margin-bottom: 20px;
}

.input-container {
  margin: 10px 0;
}

input {
  width: 250px;
  padding: 10px;
  border-radius: 20px;
  border: 2px solid #00d9ff;
  background: transparent;
  color: white;
  outline: none;
}

button {
  width: 100%;
  padding: 10px;
  border-radius: 20px;
  background: #00d9ff;
  color: white;
  border: none;
  cursor: pointer;
  margin-top: 10px;
}

.forgot-password, .signup {
  color: #00d9ff;
  margin-top: 10px;
  cursor: pointer;
}
</style>
