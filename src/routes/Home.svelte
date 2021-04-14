<script>
    import { Link } from "svelte-navigator";
    import Icon from "svelte-awesome";
    import {
        github,
        linkedinSquare,
        envelope,
        globe,
        briefcase,
    } from "svelte-awesome/icons";

    import { onMount, onDestroy } from "svelte";

    let labels = [
        `java developer`,
        `js developer`,
        `jr hacker`,
        `python developer`,
        `Fintech enthusiast`,
    ];
    let colors = [`#C70039`, `#ECC400`, `white`, `#067AE3`, `#56B500`];
    let label = labels[0];
    let color = colors[0];
    let counter = 0;

    onMount(async () => {
        fetchData();
    });

    const interval = setInterval(async () => {
        fetchData();
    }, 1900);

    async function fetchData() {
        label = labels[counter];
        color = colors[counter];
        counter++;
        if (labels.length === counter) {
            counter = 0;
        }
    }

    onDestroy(() => clearInterval(interval));
</script>

<div>
    <div class="title text-center">
        Rodrigo Rubio.
        <div class="subtitle">
            I'm <e style="color: {color};">{label}</e>
            <div class="icons">
                <a
                    style="color: white !important;text-decoration: none;"
                    href="https://github.com/RubioHaro"
                >
                    <Icon data={github} scale="2" />
                </a>
                <a
                    style="color: white !important;text-decoration: none;"
                    href="https://www.linkedin.com/in/rodrigo-rubio-haro/"
                >
                    <Icon data={linkedinSquare} scale="2" />
                </a>
                <Link
                    to="work"
                    style="color: white !important;text-decoration: none;"
                >
                    <Icon data={briefcase} scale="2" />
                </Link>
            </div>
        </div>
    </div>
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Cinzel:wght@500&family=Comfortaa&display=swap");

    :global(.title){
        vertical-align: middle;
        margin: 0;
        position: absolute;
        top: 50%;
        left: 50%;
        -ms-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
        color: white;
        font-family: "Cinzel", serif, "Comfortaa", cursive;
        transition: all 1s;
        text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
        font-size: calc(1.375rem + 1.5vw * 2);
    }

 
    .title {
        font-size: calc(1.375rem + 1.5vw * 2) !important;
    }

    .subtitle {
        font-size: calc(1.375rem + 1.5vw * 1) !important;
        text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
    }
</style>
