<template>
  <div id="app">

    <header class="header">
      <div class="header__left">
        <Logo v-if="showLogo" :theme="theme" /> 
      </div>
      
      <div class="header__right">        
        <ToggleTheme @changedTheme="themeChange" />
      </div>
    </header>

    <main class="main">
      <slot/>
    </main>

    <Footer/>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import ToggleTheme from '~/components/ToggleTheme.vue'
import Footer from '~/components/Footer.vue'

export default {
  props: {
    showLogo: { default: true }
  },
  data() {
    return {
      theme: ''
    }
  },
  mounted() {
    if (window.__theme == 'dark') this.theme = 'dark'; else this.theme = 'white'
  },
  methods: {
    themeChange(theme) {
      this.theme = theme
    }
  },
  components: {
    Logo,
    ToggleTheme,
    Footer
  }
}
</script>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: var(--header-height);
  padding: 0 calc(var(--space) / 2);
  top:0;
  z-index: 10;

  &__left,
  &__right {
    display: flex;
    align-items: center;
  }

  @media screen and (min-width: 1300px) {
    //Make header sticky for large screens
    position: sticky;
    width: 100%;
  }
}

.main {
  margin: 0 auto;
  padding: 1.5vw 15px 0;
  display: flex;
  flex-direction: row-reverse;
  justify-content: space-between;
  @media screen and (max-width: 1299px) {
    flex-direction: column;
  }
}

.footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: calc(var(--space) / 6);
  text-align: center;
  font-size: .8em;

  &__made-with {
    
    #heart {
      fill:red;
      color: red;
    }

    #coffee {
      fill: brown;
      color: brown;
    }

  }
  > span {
    margin: .35em 0 0 0;
  }

  a {
    color: currentColor;
    text-decoration: none;
  }
}
</style>
