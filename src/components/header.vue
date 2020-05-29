<template>
  <header>
    <nav>
      <router-link class="navbar__brand" to="/" tag="a">Stock Trader</router-link>
      <ul class="navbar__links">
        <li>
          <router-link to="/portfolio" tag="a" active-class="active" class="navbar__link">Portfolio</router-link>
        </li>
        <li>
          <router-link to="/stocks" tag="a" active-class="active" class="navbar__link">Stocks</router-link>
        </li>
      </ul>
    </nav>
    <div class="navbar__actions">
      <ul>
        <li>
          <a class="navbar__action" @click.prevent="endDay">End Day</a>
        </li>
      </ul>
      <ul>
        <li>
          <label class="dropdown-toggle navbar__action" @click="dropdownToggled = !dropdownToggled">Save & Load</label>
          <div class="dropdown" :style="{ display: dropdownToggled ? `block`: `none`}">
            <a class="navbar__action" @click.prevent="save">Save Data</a>
            <a class="navbar__action" @click.prevent="load">Load Data</a>
          </div>
        </li>
      </ul>
      <ul>
        <li>
          <a :style="{ color: Math.round(funds) > 0 ? 'green':'red' }" class="funds">Funds: {{ funds | monify }}</a>
        </li>
      </ul>
    </div>
    <div class="hamburger-button" @click="hamburgerToggled = !hamburgerToggled">
      <span></span>
      <span></span>
      <span></span>
    </div>
    <div class="mobile-actions" :style="{ display: hamburgerToggled ? `block`: `none` }">
      <button class="mobile-action" @click.prevent="endDay">End Day</button>
      <button class="mobile-action" @click.prevent="save">Save Data</button>
      <button class="mobile-action" @click.prevent="load">Load Data</button>
    </div>
    <div class="funds-mobile" :style="{ color: Math.round(funds) > 0 ? 'green':'red' }">Funds: {{ funds | monify }}</div>
  </header>
</template>

<script>
  import { mapGetters, mapActions } from 'vuex';

  export default {
    data() {
      return {
        dropdownToggled: false,
        hamburgerToggled: false,
      }
    },
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
   header {
    margin: 2.5rem 0;
    padding: .5rem 1rem;
    background: #f8f9fa;
    font-size: 1rem;
    position: relative;
  }

  nav {
    display: inline-block;
    width: calc(100% - 40px);
  }

  ul {
    display: inline-block;
    margin: 0;
    padding: 0;
    width: 60%;
    text-align: center;
  }

  li {
    list-style: none;
    display: inline-block;
    padding: .5rem;
    margin: 0 .5rem;
  }

  a {
    text-decoration: none;
    color: rgba(0, 0, 0, .5);
  }

  .navbar__actions {
    display: inline-block;
  }

  .navbar__brand {
    color: #212529;
    font-size: 1.25rem;
    margin-right: 1rem;
    padding: 0.3rem 0;
  }

  .navbar__link:hover {
    color:rgba(0, 0, 0, .7);
  }

  .hamburger-button {
    display: inline-block;
    width: 35px;
    border: 1px solid rgba(0, 0, 0, .2);
    border-radius: 2px;
    padding: 2px 6px;
    vertical-align: middle;
    cursor: pointer;
    position: absolute;
    top:20px;
  }

  .hamburger-button > span {
    width: 100%;
    height: 0.1rem;
    background: rgba(0, 0, 0, .7);
    display: block;
    margin: 5px 0;
    /* position: absolute; */
  }

  .funds-mobile {
    margin-top: 5px;
    font-size: .8rem;
    margin-left: 35%;
  }

  .navbar__actions {
    display: none;
  }

  .navbar__action {
    cursor: pointer;
    color: rgba(0, 0, 0, .5);
  }

  .navbar__action:hover {
    color: rgba(0, 0, 0, .7);
  }

  .dropdown-toggle::after {
    content: '';
    display: inline-block;
    margin-left: .225rem;
    vertical-align: .225rem;
    border-top: .3rem solid;
    border-right: .3rem solid transparent;
    border-bottom: 0;
    border-left: .3rem solid transparent;
  }

  .dropdown {
    position: absolute;
    border: 1px solid rgba(0, 0, 0, .3);
    border-radius: 3px;
    padding: 8px 16px;
    padding-right: 64px;
    z-index: 2;
    background: white;
    margin-top: 8px;
  }

  .dropdown > a {
    display: block;
    margin: 8px 0;
  }

  .mobile-actions {
    background: white;
    padding: 4px 0;
    margin-top: 16px;
  }

  .mobile-action {
    display: block;
    margin: 32px 0;
    margin-left: 32px;
    cursor: pointer;
    border: none;
    padding: none;
    background: transparent;
    color: rgba(0, 0, 0, .5);
  }

  .mobile-action:hover {
    color: rgba(0, 0, 0, .7);
  }

  .mobile-action:focus {
    outline: none;
  }

  @media (min-width: 38.5rem) {
    nav {
      width: calc(100% - 310px);
    }

    ul {
      width: auto;
      text-align: left;
    }

    li {
      margin: 0;
    }

    .hamburger-button {
      display: none;
    }

    .mobile-actions {
      display: none;
    }

    .funds-mobile {
      display: none;
    }

    .navbar__actions {
      display: inline-block;
    }
  }
</style>