
<script>
import GalleryItem from './GalleryItem.svelte'
import NoResults from './NoResults.svelte'

export let photos
</script>



<div class="photo-container">
    <h3>Search Results</h3>
    {#if photos.length > 0}
    <ul>
        {#each photos as photo}
         <GalleryItem
             url={`https://farm${photo.farm}.staticflickr.com/${photo.server}/${
             photo.id
             }_${photo.secret}.jpg`}
             key={photo.id}
         />
        {/each}
     </ul>
    {:else}
        <NoResults />
    {/if} 
</div>

<style>
    .photo-container ul {
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  -ms-align-items: flex-start;
  align-items: flex-start;
}

.photo-container ul li {
  max-width: 220px;
  max-height: 150px;
  overflow: hidden;
  margin-bottom: 15px;
}

.photo-container ul img {
  width: 100%;
  transition: transform 1.25s;
  box-shadow: 3px 8px 5px grey;
}

.photo-container li:hover img {
  transform: scale(1.65);
}

.photo-container .not-found {
  width: 100%;
}

@media only screen and (max-width: 767px) {
  .photo-container li {
    margin: auto;
  }
}
</style>