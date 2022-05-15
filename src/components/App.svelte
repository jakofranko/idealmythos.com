<script>
    import { onMount } from "svelte";
    import { sample } from "underscore";
    import Menu from "./Menu.svelte";
    import Home from './Home.svelte';
    import About from './About.svelte';
    import Products from './Products.svelte';
    import Contact from './Contact.svelte';
    import { page } from "../stores";

    const fonts = [
        "7em/0.8 Blackthorn, serif",
        "6em/1.2 CityCrew, serif",
        "5em DeutscheZierschrift, serif",
        "6em FranklinFracture, serif",
        "7em SwordSkull, serif",
    ];
    const font = sample(fonts);
    const backgrounds = [
        "black_glitch",
        "horizontal_glitch",
        "vertical_glitch",
    ];
    const background = sample(backgrounds);

    onMount(() => {
        const bg = document.querySelector("#background");
        bg.playbackRate = 0.5;
    });
</script>

<main style="--random-font: {font}">
    <section id="splash">
        {#if $page === 'Home'}
            <Home />
        {:else if $page === 'About'}
            <About />
        {:else if $page === 'Products'}
            <Products />
        {:else if $page === 'Contact'}
            <Contact />
        {/if}
        <div id="overlay" />
        <video
            id="background"
            src="/assets/videos/{background}.mp4"
            muted
            loop
            autoplay
        />
    </section>
    <Menu />
</main>

<style>
    #overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #121212;
        opacity: 0.3;
        z-index: 1;
    }

    #background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: 0;
    }
</style>
