<script>
    const links = [
        ["patreon", "#", ""],
        ["discord", "#", ""],
        ["instagram", "#", "invert"],
        ["kickstarter", "#", ""],
    ];
</script>

<ul id="social">
    {#each links as link}
        <li>
            <a href={link[1]}>
                <img
                    src="/assets/images/{link[0]}.png"
                    alt={link[0]}
                    class={link[2]}
                />
            </a>
        </li>
    {/each}
</ul>

<style>
    #social {
        display: flex;
        justify-content: center;
        list-style: none;
        padding: 0;
    }

    #social li {
        margin-right: 2em;
        margin-left: 2em;
    }

    #social li img {
        width: 40px;
    }

    #social li img.invert {
        filter: invert(1);
    }
</style>
