<template>
  <div>
    <nav class="navbar navbar-light">
      <div class="container">
        <nuxt-link class="navbar-brand" to="/">Home</nuxt-link>
        <ul class="nav navbar-nav pull-xs-right">
          <template v-if="user">
            <li class="nav-item">
              <!-- Add "active" class when you're on that page" -->
              <nuxt-link class="nav-link" to="/" exact>Home</nuxt-link>
            </li>
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/edit" exact>
                <i class="ion-compose"></i>&nbsp;New Article
              </nuxt-link>
            </li>
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/settings" exact>
                <i class="ion-gear-a"></i>&nbsp;Settings
              </nuxt-link>
            </li>
            <li class="nav-item">
              <nuxt-link class="nav-link" :to="'/profile/' + user.username" exact>
                <img class="user-pic" :src="user.image" alt="" />
                {{ user.username }}
              </nuxt-link>
            </li>
          </template>
          <template v-if="!user">
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/login" exact>Sign in</nuxt-link>
            </li>
            <li class="nav-item">
              <nuxt-link class="nav-link" to="/register" exact>Sign up</nuxt-link>
            </li>
          </template>
        </ul>
      </div>
    </nav>
    <nuxt-child />
    <footer>
      <div class="container">
        <a href="/" class="logo-font">conduit</a>
        <span class="attribution">
          An interactive learning project from
          <a href="https://thinkster.io">Thinkster</a>. Code &amp; design licensed under
          MIT.
        </span>
      </div>
    </footer>
  </div>
</template>
<script>
import { mapState } from "vuex";
export default {
  name: "layout",
  computed: {
    ...mapState(["user"]),
  },
};
</script>
<style lang=""></style>
