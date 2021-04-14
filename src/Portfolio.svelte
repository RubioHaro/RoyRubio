<script>
    import { Link } from "svelte-navigator";
    import Icon from "svelte-awesome";
    import { arrowLeft } from "svelte-awesome/icons";
</script>

<div>
    <div class="title text-center">
        Rodrigo Rubio Projects
        <div class="subtitle text-center">
            <Link
                to="/"
                style="color: white !important;text-decoration: none;"
            >
                <Icon data={arrowLeft} scale="2" /> Go back
            </Link>
        </div>
    </div>
</div>

<style>
     .subtitle {
        font-size: calc(1rem + 1vw * 1) !important;
        text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
    }
</style>
