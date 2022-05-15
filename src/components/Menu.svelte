<script>
    import { page } from "../stores";

    const pages = [
        "Home",
        "About",
        // 'Products',
        "Contact",
    ];

    function handleToggle(event) {
        const element = event.currentTarget;
        element.classList.toggle("on");
        const splash = document.getElementById("splash");
        splash.classList.toggle("shift");
    }

    function handleClick(event) {
        const {
            target: {
                dataset: { nav },
            },
        } = event;
        const splash = document.getElementById("splash");
        const toggle = document.getElementById("toggle");

        page.set(nav);
        toggle.classList.toggle("on");
        splash.classList.toggle("shift");
    }
</script>

<!-- these styles are in the global css file -->
<a href="#menu" id="toggle" on:click={handleToggle}><span /></a>
<div id="menu">
    <ul>
        {#each pages as page}
            <li data-nav={page} on:click={handleClick}>{page}</li>
        {/each}
    </ul>
</div>

<!-- Toggle menu inspired by https://codepen.io/GeoffreyCrofte/pen/nybYBm -->
<style>
    #menu {
        position: absolute;
        top: 0;
        right: 0;
        width: var(--menu-width);
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all 0.2s;
        z-index: -1;
    }

    #menu ul {
        list-style: none;
        position: relative;
        padding: 0;
        margin: 0;
    }

    #menu ul li {
        line-height: 2em;
        color: var(--white);
        font-size: 1.2em;
        cursor: pointer;
    }
</style>
