
<script>
    import { Link } from "svelte-routing";
    export let search
</script>

  <nav class="main-nav">
    <ul>
      <li>
        <Link
          on:click={() => search("trains")}
          activeStyle={{ backgroundColor: "tomato" }}
          to="/trains"
        >
          Trains
        </Link>
      </li>
      <li>
        <Link
            on:click={() => search("people")}
          activeStyle={{ backgroundColor: "green" }}
          to="/people"
        >
          People
        </Link>
      </li>
      <li>
        <Link on:click={() => search("planes")} to="/planes">
          Planes
        </Link>
      </li>
    </ul>
  </nav>

<style>
    .main-nav li {
  width: 100%;
  margin-bottom: 1em;
}

.main-nav a {
  display: block;
  background: #438bbd;
  border-radius: 3px;
  padding: 5px;
  color: #fff;
}

.main-nav .active,
.main-nav a:hover,
.search-form button:hover {
  background-color: #275270;
  -webkit-animation: swing 1s ease;
  animation: swing 1s ease;
  -webkit-animation-iteration-count: 1;
  animation-iteration-count: 1;
}

@media only screen and (min-width: 768px) {
  .main-nav ul {
    display: flex;
    justify-content: center;
  }

  .main-nav li {
    margin: 10px;
    width: 100px;
  }
}
</style>
