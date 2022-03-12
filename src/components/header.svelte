
<script>
    import Nav from './Nav.svelte'
    import SearchForm from './SearchForm.svelte'

    export let photos
    export let onSearch = () => {}
    export let updateText = () => {}

</script>

<h1>Gallerize</h1>
    <h3>
        <em>A Svelete Photo Gallery App</em>
    </h3>
    <SearchForm onSearch={onSearch} photos={photos} />
    <Nav search={onSearch} />

