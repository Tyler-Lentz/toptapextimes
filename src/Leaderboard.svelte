<script lang="ts">
    import {slide} from 'svelte/transition';

    class Entry {
        name: string;
        time: number; // seconds
        start_time: string;
        end_time: string;
        order_number: number;
        proof: string; // link

        constructor(name: string, time: number, start_time: string, end_time: string, order_number: number, proof: string) {
            this.name = name;
            this.time = time;
            this.start_time = start_time;
            this.end_time = end_time;
            this.order_number = order_number;
            this.proof = proof;
        }

        getTableRow() {
            return `<tr>
                <td>${this.name}</td>    
                <td>${this.time}</td>    
                <td>${this.start_time}</td>    
                <td>${this.end_time}</td>    
                <td>${this.order_number}</td>    
                <td>${this.proof}</td>    
            </tr>`
        }
    }

    const data = [
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
        new Entry("David Nielsen", 10, "3/6/2023 9:15:13 PM", "3/6/2023 9:15:23 PM", 4012595, "https://drive.google.com/file/d/15EYi6EQ_C0QEiHkVdgLxV9Nye-SnEiMB/view?usp=share_link"),
    ]

    export let num_shown = 5;
</script>

<button on:click={() => num_shown+=5}>Add</button>
<button on:click={() => num_shown-=5}>Sub</button>
<table>
    <tr>
        <th>Place</th>
        <th>Name</th>
        <th>Time</th>
        <th>Start Time</th>
        <th>End Time</th>
        <th>Order Number</th>
        <th>Proof</th>
    </tr>
    {#each data as row, i}
        {#if i < num_shown}
            <tr transition:slide>
                <td>{i+1}.</td>
                <td>{row.name}</td>
                <td>{row.time}</td>
                <td>{row.start_time}</td>
                <td>{row.end_time}</td>
                <td>{row.order_number}</td>
                <td><a href={row.proof}>Click here</a><img src="svg/cursor.svg" alt="cursor"></td>
            </tr>
        {/if}
    {/each}
</table>

<style>
    table {
        color: var(--text-dark-color);
        background-color: var(--highlight-color);
        border-radius: 1rem;
        text-align: center;
        padding: 2rem;
    }
    tr {
        display: block;
    }
    td {
        padding: 0.5rem;
        color: var(--text-light-color);
    }
    a {
        color: var(--text-dark-color);
    }
</style>