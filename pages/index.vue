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
      
      <div id="_youtube-iframe-wrapper">
		    <div id="_youtube-iframe" data-youtubeurl="0vrdgDdPApQ">
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
    
  var tag = document.createElement('script');
	tag.src = "https://www.youtube.com/iframe_api";
	var firstScriptTag = document.getElementsByTagName('script')[0];
	firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

	// 3. This function creates an <iframe> (and YouTube player)
	//    after the API code downloads.
	var youtubePlayer;
	var _youtube_id = document.getElementById('_youtube-iframe');
	
	function onYouTubeIframeAPIReady() {				
		youtubePlayer = new YT.Player('_youtube-iframe', {
			videoId: _youtube_id.dataset.youtubeurl,
			playerVars: { // https://developers.google.com/youtube/player_parameters?playerVersion=HTML5
				cc_load_policy: 0, // closed caption
				controls: 0,
				disablekb: 0, //disable keyboard
				iv_load_policy: 3, // annotations
				playsinline: 1, // play inline on iOS
				rel: 0, // related videos
				showinfo: 0, // title
				modestbranding: 3 // youtube logo
			},
			events: {
				'onReady': onYoutubePlayerReady,
				'onStateChange': onYoutubePlayerStateChange
			}
		});
	}
	
	function onYoutubePlayerReady(event) {
		event.target.mute();
		event.target.playVideo();				
	}


  }
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


#youtube-iframe-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  position: absolute;
  height: 100%;
  background-color: navy;
}
#youtube-iframe {
  position: absolute;
  pointer-events: none;
  margin: 0 auto;
  height: 300vh; 
  width: 120vw;	
}
</style>
