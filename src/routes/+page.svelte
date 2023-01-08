<script lang="ts">
    import Navbar from '../components/Navbar.svelte';
    import HomeSketch from '../sketches/HomeSketch.svelte';
</script>

<header>
    <Navbar page="/" />
</header>

<HomeSketch />
<div id="box">
    <img src="/assets/images/dp.png" alt="DP" id="dp" />
    <h1><u>Joshua Gardner</u></h1>
    <h3><em>Integrated Application Development</em></h3>
    <p>
        Swinburne University of Technology
        <br />
        Bachelor of Computer Science - Professional
        <br />
        Major: Software Design
        <br />
        Minor: Applied Mathematics
    </p>
    <!-- svelte-ignore a11y-missing-content -->
    <a href="https://github.com/jgardn3r" class="fa fa-github" title="GitHub" />
    <!-- svelte-ignore a11y-missing-content -->
    <a
        href="https://www.linkedin.com/in/joshua-gardner-7441301b1/"
        class="fa fa-linkedin"
        title="LinkedIn"
    />
</div>

<style lang="css">
    @font-face {
        font-family: VulfSans;
        src: URL('/assets/fonts/Vulf_Sans-Regular.woff') format('woff'),
            /* Chrome 6+, Firefox 3.6+, IE 9+, Safari 5.1+ */
                URL('/assets/fonts/Vulf_Sans-Regular.ttf') format('truetype');
        /* Chrome 4+, Firefox 3.5, Opera 10+, Safari 3—5 */
    }

    @media screen and (max-height: 600px) {
        #dp {
            display: none;
        }
    }

    @media screen and (min-height: 600px) {
        #dp {
            display: block;
        }
    }

    #dp {
        border-radius: 50%;
        border: 0px solid white;
        margin-left: auto;
        margin-right: auto;
        width: 50%;
        max-width: 200px;
        min-width: 200px;
        z-index: -1;
    }

    #box {
        position: absolute;
        left: 50%;
        top: 50%;
        width: 50%;
        transform: translate(-50%, -50%);
        color: white;
        text-align: center;
        min-width: 335px;
    }

    #box h1 {
        font-size: 1.5em;
        font-family: VulfMono;
    }

    #box h3,
    p {
        font-size: 1em;
    }

    #box p,
    h3 {
        font-family: VulfSans;
    }

    #box .fa:hover {
        opacity: 0.7;
    }

    #box .fa-linkedin {
        background: #007bb5;
        color: white;
    }

    #box .fa-github {
        background-color: #24292e;
        color: white;
    }

    #box .fa {
        padding: 20px;
        font-size: 30px;
        width: 30px;
        text-align: center;
        text-decoration: none;
    }
</style>
