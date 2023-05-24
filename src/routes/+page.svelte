<script lang="ts">
    import MyNavbar from "../MyNavbar.svelte";
    import Leaderboard from "../Leaderboard.svelte";

    let num_shown: number;
</script>

<MyNavbar curr_page="Leaderboard"/>
<main>
    <h1>Top {num_shown} Tapex Times</h1>
    <Leaderboard bind:num_shown/>
</main>

<style>
    h1 {
        color: var(--text-light-color);
        text-align: center;
        font-size: 3rem;
    }

    main {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
</style>