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

    function handleToggle(event) {
        const element = event.currentTarget;
        element.classList.toggle("on");
    }
</script>

<main style="--random-font: {font}">
    <section id="splash">
        <h1 id="title">{title}</h1>
        <div id="overlay" />
        <video
            id="background"
            src="/assets/videos/{background}.mp4"
            muted
            loop
            autoplay
        />
        <ul id="social">
            <li><img src="/assets/images/patreon.png" alt="patreon" /></li>
            <li><img src="/assets/images/discord.png" alt="discord" /></li>
            <li><img src="/assets/images/instagram.png" alt="instagram" /></li>
            <li>
                <img src="/assets/images/kickstarter.png" alt="kickstarter" />
            </li>
        </ul>
    </section>

    <a href="#menu" id="toggle" on:click={handleToggle}><span /></a>
    <div id="menu">
        <ul>
            <li><a href="#">About</a></li>
            <li><a href="#">Products</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </div>
</main>

<!-- Toggle menu inspired by https://codepen.io/GeoffreyCrofte/pen/nybYBm -->
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
        z-index: 2;
        font: var(--random-font);
    }

    #overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #121212;
        z-index: 1;
    }

    #background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        opacity: 0.8;
        z-index: 0;
    }

    #social {
        display: flex;
        list-style: none;
        z-index: 3;
    }

    #social li {
        margin-right: 2em;
    }

    #social li img {
        width: 40px;
    }

    #toggle {
        position: absolute;
        top: 20px;
        right: 20px;
        display: block;
        width: 28px;
        height: 30px;
        margin: 30px auto 10px;
        z-index: 4;
    }
    #toggle span:after,
    #toggle span:before {
        content: "";
        position: absolute;
        left: 0;
        top: -9px;
    }
    #toggle span:after {
        top: 9px;
    }
    #toggle span {
        position: relative;
        display: block;
    }
    #toggle span,
    #toggle span:after,
    #toggle span:before {
        width: 100%;
        height: 5px;
        background-color: #ddd;
        transition: all 0.3s;
        backface-visibility: hidden;
        border-radius: 2px;
    }

    /* on activation */
    #toggle.on span {
        background-color: transparent;
    }
    #toggle.on span:before {
        transform: rotate(45deg) translate(5px, 5px);
    }
    #toggle.on span:after {
        transform: rotate(-45deg) translate(7px, -8px);
    }
    #toggle.on + #menu {
        opacity: 1;
        visibility: visible;
    }
</style>
