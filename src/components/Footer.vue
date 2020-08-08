<template>
    <footer class="footer">
      <span class="footer__made-with">Made with 
        <!-- <svg id="heart" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-heart">
          <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path>
        </svg> -->
        <span title="love">❤️</span>
        and
        <!-- <svg id="coffee" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-coffee">
          <path d="M18 8h1a4 4 0 0 1 0 8h-1"></path>
          <path d="M2 8h16v9a4 4 0 0 1-4 4H6a4 4 0 0 1-4-4V8z"></path>
          <line x1="6" y1="1" x2="6" y2="4"></line><line x1="10" y1="1" x2="10" y2="4"></line>
          <line x1="14" y1="1" x2="14" y2="4"></line>
        
        </svg> -->
        <span title="coffee">☕️</span>
        <a href="https://www.google.com/maps/place/Tripoli/@32.8829717,13.1708262,14z/data=!3m1!4b1!4m5!3m4!1s0x13a892c4c11c43d9:0x8d99d8947b5cec86!8m2!3d32.8872094!4d13.1913383"
        target="__blank" rel="noreferrer noopener">in Tripoli, Libya </a>
      </span>
      <span class="footer__links"><span title="powered">⚡️</span> by 
        <a href="//gridsome.org" target="__blank" rel="noreferrer noopener"> Gridsome</a>, 
        <a href="//forestry.io" target="__blank" rel="noreferrer noopener"> Forestry</a> and
        <a href="//cloudinary.com" target="__blank" rel="noreferrer noopener"> Cloudinary </a>
        <span title="deployed" style="margin-left: 1em;">🚀</span> on <a href="//netlify.com" target="__blank" rel="noreferrer noopener">Netlify</a>
        </span>
        
    </footer>
</template>

<style lang="scss" scoped>
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