<script>
    import { onMount } from "svelte";
    import { sample } from "underscore";
    const title = "Ideal Mythos";
    const fonts = [
        "7em Blackthorn, serif",
        "6em CityCrew, serif",
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
        <h1 id="title">{title}</h1>
        <video
            id="background"
            src="/assets/videos/{background}.mp4"
            muted
            loop
            autoplay
        />
        <ul id="social">
            <li><img src="" alt="patreon" /></li>
            <li><img src="" alt="instagram" /></li>
        </ul>
    </section>
</main>

<style>
    #splash {
        position: absolute;
        right: 0;
        width: 100%;
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background: #010101;
        color: #fdfdfd;
    }

    h1 {
        z-index: 999;
        font: var(--random-font);
    }

    #background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        opacity: 0.8;
    }

    #social {
        display: flex;
        list-style: none;
    }

    #social li {
        margin-right: 2em;
    }
</style>
