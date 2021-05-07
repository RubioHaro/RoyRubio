<script>
    import { Link } from "svelte-navigator";
    import Icon from "svelte-awesome";
    import { fadeIn, fadeOut } from "./component/pageFade";
    import { arrowLeft } from "svelte-awesome/icons";
    import {
        Col,
        Container,
        Row,
        Card,
        CardBody,
        CardHeader,
        CardSubtitle,
        CardText,
        CardTitle,
        Carousel,
        CarouselControl,
        CarouselIndicators,
        CarouselItem,
        CarouselCaption,
    } from "sveltestrap";

    import Proyect from "./component/Proyect.svelte";

    const items = [
        {
            img: "/img/blog.png",
            title: "Blog",
            focus: { x: 0, y: 0 },
            content: "EL blog es cute",
        },
        {
            img: "/img/linearity.png",
            title: "Linearity",
            focus: { x: 50, y: 20 },
            content: "Linearity",
        },
        {
            img: "/img/artic.png",
            title: "Artic Breaker",
            focus: { x: 80, y: 55 },
            content: "El Script",
        },
    ];
    let activeIndex = 0;
    let open = [false, false, false];

    function toogle(o) {
        for (let e = 0; e < open.length; e++)
            (open[e] = !1), e === o && (open[e] = !0);
    }
</script>

<div in:fadeIn out:fadeOut>
    <div class="title text-center">
        Rodrigo Rubio Projects
        <div class="proyectos pt-2">
            <Carousel {items} bind:activeIndex ride={true} interval={2000}>
                <CarouselIndicators bind:activeIndex {items} />

                <div class="carousel-inner">
                    {#each items as item, index}
                        <CarouselItem bind:activeIndex itemIndex={index}>
                            <Card on:click={() => toogle(index)}>
                                <!-- <Card> -->
                                <CardHeader>
                                    {item.title}
                                </CardHeader>
                                <img
                                    src={item.img}
                                    class="img-fluid"
                                    alt={item.title}
                                    style="object-position: {item.focus
                                        .x}% {item.focus.y}% !important; "
                                />
                            </Card>
                        </CarouselItem>
                        <Proyect proyect={items[index]} open={open[index]} />
                    {/each}
                </div>

                <CarouselControl direction="prev" bind:activeIndex {items} />
                <CarouselControl direction="next" bind:activeIndex {items} />
            </Carousel>
        </div>
        <div class="subtitle text-center">
            <Link to="/" style="color: white !important;text-decoration: none;">
                <Icon data={arrowLeft} scale="2" /> Go back
            </Link>
        </div>
    </div>
</div>

<style>
    /* OPEA */
    /* :global(.custom-button) {
        display: none !important;
    } */
    :global(.modal) {
        overflow: hidden !important;
    }

    @media (max-width: 480px) {
        img {
            width: 80vw !important;
        }
    }
    img {
        height: 50vh;
        width: 100%;
        background-position: center 10px;
        object-fit: cover;
        object-position: 50% 5%;
        opacity: 0.8;
        max-width: none;
        overflow: auto;
    }
    .subtitle {
        font-size: calc(1rem + 1vw * 1) !important;
        text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
    }

    .proyectos {
        cursor: pointer;
        /* position: absolute; */
        font-size: calc(1rem + 1vw * 0.5) !important;
        text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
    }
</style>
