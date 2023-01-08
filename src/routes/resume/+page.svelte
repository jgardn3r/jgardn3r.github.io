<script lang="ts">
    import Navbar from '../../components/Navbar.svelte';
</script>

<header>
    <Navbar page="resume" />
</header>
<iframe
    src="https://drive.google.com/file/d/1PEtO5SSLE-Qz0ooL3zDzznJucwQwvtrk/preview"
    title="Resume">Resume Preview</iframe
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
