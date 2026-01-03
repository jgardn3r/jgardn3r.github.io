<script lang="ts">
    export let page: string;

    let navbarResponsive = false;

    type Page = {
        name: string;
        path: string;
    };
    let pages: Page[] = [
        {
            name: 'Home',
            path: '/',
        },
        {
            name: 'Résumé',
            path: 'resume',
        },
        {
            name: 'Theatre',
            path: 'theatre',
        },
        {
            name: 'Contact',
            path: 'mailto:joshgardner2000@gmail.com',
        },
    ];
</script>

<svelte:head>
    <title
        >{pages.filter((pageObj) => pageObj.path == page).map((pageObj) => pageObj.name)[0]} | Joshua
        Gardner</title
    >
    <link
        rel="stylesheet"
        href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"
    />
</svelte:head>

<div class="navbar {navbarResponsive ? ' responsive' : ''}">
    {#each pages as pageObject}
        <a class={page == pageObject.path ? 'active' : ''} href={pageObject.path}
            >{pageObject.name}</a
        >
    {/each}
    <span class="sanga">
        <!-- svelte-ignore a11y-invalid-attribute -->
        <a
            href="javascript:void(0)"
            class="icon sanga"
            on:click={() => (navbarResponsive = !navbarResponsive)}
        >
            <i class="fa fa-bars" />
        </a>
    </span>
</div>

<style lang="css">
    @font-face {
        font-family: VulfMono;
        src: URL('/assets/fonts/Vulf_Mono-Regular_web.woff') format('woff'),
            /* Chrome 6+, Firefox 3.6+, IE 9+, Safari 5.1+ */
                URL('/assets/fonts/Vulf_Mono-Regular_web.ttf') format('truetype');
        /* Chrome 4+, Firefox 3.5, Opera 10+, Safari 3—5 */
    }

    :global(body) {
        margin: 0;
        height: 100vh;
    }

    div {
        margin: 0;
        font-family: VulfMono;
    }

    .navbar {
        overflow: hidden;
        z-index: 2;
        /* background-color: #333; */
    }

    .navbar a {
        float: left;
        display: block;
        color: #fff;
        text-align: center;
        padding: 14px 16px;
        text-decoration: none;
        font-size: 17px;
    }

    .navbar a:not(.sanga):hover::after {
        content: '';
        display: block;
        padding: 2px 0;
        margin: -3px 0;
        line-height: 1px;
        border-bottom: 2px solid #fff;
    }

    .navbar a.active {
        background-color: #fff;
        color: #343434;
    }

    .navbar .icon {
        display: none;
    }

    @media screen and (max-width: 600px) {
        .navbar a:not(:first-child) {
            display: none;
        }

        .navbar a.icon {
            float: right;
            display: block;
            padding-top: 20px;
        }
    }

    @media screen and (max-width: 600px) {
        .navbar.responsive {
            position: relative;
        }

        .navbar.responsive .icon {
            position: absolute;
            right: 0;
            top: 0;
        }

        .navbar.responsive a:not(.sanga) {
            float: none;
            display: block;
            text-align: left;
            background-color: #343434;
        }

        .navbar.responsive a.active {
            background-color: white;
        }
    }
</style>
