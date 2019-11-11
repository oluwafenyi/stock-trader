<template>
  <header class="navigation-bar">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <router-link class="navbar-brand" to="/" tag="a">Stock Trader</router-link>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown"
        aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link to="/portfolio" tag="a" class="nav-link" active-class="active">Portfolio</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/stocks" tag="a" active-class="active">Stocks</router-link>
        </li>
      </ul>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <a class="nav-link" style="cursor: pointer;" @click.prevent="endDay">End Day</a>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button"
              data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              Save & Load
            </a>
            <div class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
              <a class="dropdown-item" style="cursor: pointer;" @click.prevent="save">Save Data</a>
              <a class="dropdown-item" style="cursor: pointer;" @click.prevent="load">Load Data</a>
            </div>
          </li>
          <li class="nav-item">
            <a class="nav-link">Funds: {{ funds | monify }}</a>
          </li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script>
  import { mapGetters, mapActions } from 'vuex';

  export default {
    computed: {
      ...mapGetters([
        'funds'
      ]),
    },
    methods: {
      ...mapActions([
        'endDay',
        'save',
        'load',
      ]),
    }
  }
</script>

<style scoped>
   header.navigation-bar {
    margin: 40px 0;
  }
</style>