<template>
  <div
    class="container"
    :class="{'light-background' : !isDarkMode, 'dark-background' : isDarkMode}"
  >
    <RequestAccount />
    <div class="login">
      <img src="@/assets/vplogo.svg" v-show="isDarkMode" />
      <img src="@/assets/vplogo-dark.svg" v-show="!isDarkMode" />
      <h4 :class="{'light-text' : isDarkMod, 'dark-text' : !isDarkMode}">Sign into VP</h4>
      <input
        type="email"
        placeholder="Email"
        :class="{'light-field' : isDarkMode, 'dark-field' : !isDarkMode}"
      />
      <input
        type="password"
        placeholder="Password"
        :class="{'light-field' : isDarkMode, 'dark-field' : !isDarkMode}"
      />
      <button>Sign In</button>
      <router-link
        to="/recover"
        :class="{'light-link' : isDarkMode, 'dark-link' : !isDarkMode}"
      >Forgot your password?</router-link>
      <ThemeSwitch />
    </div>
  </div>
</template>

<script>
import RequestAccount from "@/components/RequestAccount";
import ThemeSwitch from "@/components/ThemeSwitch";

export default {
  name: "SignIn",
  components: {
    RequestAccount,
    ThemeSwitch
  },
  computed: {
    isDarkMode() {
      return this.$store.getters.isDarkMode;
    }
  },
  methods: {
    toggleDarkMode() {
      this.$store.commit("tottgleDarkMode");
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;

  min-height: 100vh;
}
.login {
  width: 400px;
}
</style>
