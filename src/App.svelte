
<script>
	import { onMount } from "svelte";
	import { Router, Route } from "svelte-routing";
	import { API_KEY } from "./config";
	import axios from 'axios'
	import Header from './components/header.svelte'
	import Gallery from './components/Gallery.svelte'
	import NotFound from './components/NotFound.svelte'


	let photos = []
	let loading = true
	let text = 'cars'

const performSearch = async (search = text) => {
	
	loading = true

	try {
		const res = await axios.get(
        `https://www.flickr.com/services/rest/?method=flickr.photos.search&api_key=${API_KEY}&tags=${search}&per_page=24&format=json&nojsoncallback=1`
      )
		if (res.data.photos && res.data.photos.photo.length > 0) {
			console.log(res.data.photos)
			photos = res.data.photos.photo
			loading = false
		}
	} catch (e) {
		console.log("Error fetching and parsing data", e);
	}
  };
  // update text in nav to show photos in links
  const shouldUpdateText = query => {
	text = query
    performSearch(query);
  };

  onMount(async () => {
	  await performSearch(text)
  })

</script>


 


  
      <Router>
        <div class="container">
          <Header
			photos={photos}
			onSearch={performSearch}
			updateText={shouldUpdateText}
		  />
			
		  {#if loading}
		  	<h2>Loading....</h2>
		  {:else}
		  <Route
		  path="/"><Gallery photos={photos} /></Route>
		<Route
		  path="/search"><Gallery photos={photos} /></Route>
		<Route
		  path="/trains"><Gallery photos={photos} /></Route>
		<Route
		  path="/people"><Gallery photos={photos} /></Route>
		<Route
		  path="/planes"><Gallery photos={photos} /></Route>
		<Route component="{NotFound}" />
		  {/if}
        
        </div>
      </Router>

	  <style>
		@media only screen and (min-width: 768px) {
			.container {
				max-width: 960px;
				margin: auto;
			}
		}
	  </style>