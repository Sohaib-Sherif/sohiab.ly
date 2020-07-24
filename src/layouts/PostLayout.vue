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

    <footer class="footer">
      <span class="footer__made-with">Made with 
        <!-- <svg id="heart" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-heart">
          <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path>
        </svg> -->
        <span title="heart">❤️</span>
        and
        <!-- <svg id="coffee" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-coffee">
          <path d="M18 8h1a4 4 0 0 1 0 8h-1"></path>
          <path d="M2 8h16v9a4 4 0 0 1-4 4H6a4 4 0 0 1-4-4V8z"></path>
          <line x1="6" y1="1" x2="6" y2="4"></line><line x1="10" y1="1" x2="10" y2="4"></line>
          <line x1="14" y1="1" x2="14" y2="4"></line>
        
        </svg> -->
        <span title="coffee">☕️</span>
        in Tripoli, Libya 
      </span>
      <span class="footer__links"><span title="powered">⚡️</span> by 
        <a href="//gridsome.org" target="__blank" rel="noreferrer noopener"> Gridsome</a>, 
        <a href="//forestry.io" target="__blank" rel="noreferrer noopener"> Forestry</a> and
        <a href="//cloudinary.com" target="__blank" rel="noreferrer noopener"> Cloudinary </a>
        </span>
    </footer>

  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import ToggleTheme from '~/components/ToggleTheme.vue'

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
    ToggleTheme
  }
}
</script>

<style lang="scss" scoped>
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
  flex-direction: column;
}

.footer {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: calc(var(--space) / 6);
  text-align: center;
  font-size: .8em;
  position: relative;
  top:7.5em;
  @media screen and (max-width: 650px) {
			top: 11em;
		}

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
