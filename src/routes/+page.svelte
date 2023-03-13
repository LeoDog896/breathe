<script lang="ts">
	import Circle from "../lib/Circle.svelte";
    import { fly } from 'svelte/transition';
	import { onMount } from "svelte";

    let state: "name" | "play" | "none" = "none"

    onMount(() => {
        state = "name"
    })
</script>

{#if state == "name"}
    <main transition:fly="{{ y: 200, duration: 2000 }}">
        <h1>Hello there. What's your name?</h1>
        <input />
    </main>
{:else if state == "play"}
    <Circle />
{/if}

<style>
    main {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        display: flex;
        flex-direction: column;
    }
</style>