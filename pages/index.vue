<template>
  <div class="container">
    <header>
      <h1 class="logo">
        utkucum
      </h1>
      <div class="navbar">
        <nuxt-link to="/">
          Ana Sayfa
        </nuxt-link>
        <nuxt-link
          to="blog"
        >
          Blog
        </nuxt-link>
        <nuxt-link
          to="work"
        >
          Work
        </nuxt-link>
      </div>
    </header>
    <main>
      <div >
        <div class="_pattern-overlay"></div>
        <div id="youtube-iframe-wrapper">
          <youtube video-id="0vrdgDdPApQ" :player-vars="player1" :mute="mute" @ended="ended"></youtube>
        </div>
      </div>
    </main>
    <footer>
      footer
    </footer>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'



export default {
  data(){
    return{
      mute: false,
      player1: {
        autoplay: 1,
        cc_load_policy: 0, // closed caption
				controls: 0,
				disablekb: 0, //disable keyboard
				iv_load_policy: 3, // annotations
				playsinline: 1, // play inline on iOS
				rel: 0, // related videos
				showinfo: 0, // title
        modestbranding: 1, // youtube logo
        loop:1,
        start: 0
      },
    }
  },
  methods:{
    ended () {
      console.log('Ended');
      this.$set(this.player1, 'start', 10)
    }
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
  components: {
    Logo
  },
  mounted() {
    console.log("mounted oldu mu");

       // Load the IFrame Player API code asynchronously.
  

  },

  
}
</script>

<style>

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
.container{
  display: grid;
  grid-template-areas:
    "header"
    "content"
    "footer";

  grid-template-columns: auto;
  grid-template-rows: auto 1fr auto;
  grid-gap: 10px;
  height: 100vh;
  padding: 10px 20px;
  background-color: #fff000;
}


header{
  grid-area: header;
  background-color: orangered;
  display:grid;
  grid-template-columns: 1fr auto auto;
  justify-items: start;
}
.navbar{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  justify-items: end;
  align-items: center;
}
main{
  grid-area: content;
  background-color: orange;
}

footer{
  grid-area: footer;
  background-color: red;
}

.fullscreen-video-background {
  background: #000;
  position: relative;
  width: 100%;
  z-index: -99;
	overflow: hidden;
  height: 100vh;
}
._pattern-overlay { 
		position: absolute;
		top: 0;
		width: 100%;
		opacity: 0.3;
		bottom: 0;
		background-image: url(https://cdnjs.cloudflare.com/ajax/libs/vegas/2.3.1/overlays/03.png);
		z-index: 2;
}

#_buffering-background {
		position: absolute;
		width: 100%;
		top: 0;
		bottom: 0;
		background: #222;
		z-index: 1;
}

#youtube-iframe-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  position: absolute;
  height: 100%;
  background-color: navy;
}
#youtube-player-1{
position: absolute;
    top: 50%;
    left: 50%;
    min-width: 100%;
    min-height: 100%;
    width: auto;
    height: auto;
    z-index: 0;
    transform: translateX(-50%) translateY(-50%);
}
</style>
