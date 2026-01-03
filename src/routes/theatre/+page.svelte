<script lang="ts">
    import Navbar from '../../components/Navbar.svelte';
</script>

<header>
    <Navbar page="theatre" />
</header>
<iframe
    src="https://drive.google.com/file/d/1cFh3xh1FijeovQMePv6h_lfv6VIjPZSI/preview"
    title="Theatre Resume">Theatre Resume Preview</iframe
>

<style lang="css">
    :global(body) {
        background: #323232;
        display: flex;
        flex-flow: column;
    }
    iframe {
        flex: 1 1 auto;
        width: 100%;
        max-width: 1250px;
        margin: auto;
        display: block;
    }
</style>
