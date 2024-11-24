<template>
    <div class="idk">
        <nav>
      <ul class="nav">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/login">Login</router-link></li>
      </ul>
    </nav>
    <div class="login-section">
      <div class="login-container">
        <h2 class="welcome-message">Create Your Account</h2>
        <form @submit.prevent="validateSignupForm">
          <input
            id="email"
            v-model="email"
            placeholder="Email"
            required
            type="email"
          />
          <input
            id="password"
            v-model="password"
            placeholder="Password"
            required
            type="password"
          />
          <p id="validation-message" class="error-message">{{ validationMessage }}</p>
          <button class="signup-btn" type="submit">Sign Up</button>
        </form>
      </div>
    </div>
    </div>
</template> 
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      validationMessage: "",
    };
  },
  methods: {
    validateSignupForm() {
      this.validationMessage = ""; // Reset the validation message
      const errors = [];

      // Validation rules
      if (this.password.length < 8 || this.password.length >= 15) {
        errors.push("Password must be at least 8 characters and less than 15 characters long.");
      }
      if (!/^[A-Z]/.test(this.password)) {
        errors.push("Password must start with an uppercase alphabet character.");
      }
      if (!/[A-Z]/.test(this.password)) {
        errors.push("Password must include at least one uppercase alphabet character.");
      }
      if ((this.password.match(/[a-z]/g) || []).length < 2) {
        errors.push("Password must include at least two lowercase alphabet characters.");
      }
      if (!/\d/.test(this.password)) {
        errors.push("Password must include at least one numeric value.");
      }
      if (!/_/.test(this.password)) {
        errors.push("Password must include the character '_'.");
      }

      // Set validation message or proceed
      if (errors.length > 0) {
        this.validationMessage = "The password is not valid - " + errors.join(" ");
      } else {
        alert("Account successfully created!");
        // Redirect or clear the form after success
        this.email = "";
        this.password = "";
      }
    },
  },
};
</script>

<style scoped>
/* Styles for navigation */
.nav {
  list-style: none;
  padding: 0;
  display: flex;
  gap: 10px;
}

.nav li {
  display: inline-block;
}

.nav a {
  text-decoration: none;
  color: blue;
}

/* Styles for the form */
.login-section {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f9f9f9;
}

.login-container {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  width: 300px;
  text-align: center;
}

.welcome-message {
  margin-bottom: 20px;
}

input {
  display: block;
  width: 100%;
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.signup-btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
}

.signup-btn:hover {
  background-color: #0056b3;
}

.error-message {
  color: red;
  font-size: 0.9rem;
  margin-bottom: 10px;
}
</style>