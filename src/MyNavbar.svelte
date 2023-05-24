<script lang="ts">
    export let curr_page: string;

    const pages = [
        {label: "Leaderboard", href: "/"},
        {label: "Form", href: "/form"},
        {label: "Data", href: "/data"}
    ];
</script>

<nav>
    {#each pages as page}
        <a href={page.href} data-current={curr_page === page.label}>{page.label}</a>
    {/each}
</nav>

<style>
    nav {
        background-color: var(--bg-dark-color);
        color: var(--text-light-color);
        display: flex;
        flex-direction: row;
        justify-content: center;
    }

    a {
        padding-right: 1rem;
        padding-left: 1rem;
        color: var(--highlight-color);
    }

    a[data-current="true"] {
        color: var(--highlight-color);
        text-decoration: underline;
    }
    a[data-current="false"] {
        text-decoration: none;
    }

    a:not(:last-child) {
        border-right: 1px solid var(--highlight-color);
    }
</style>