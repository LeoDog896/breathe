<script lang="ts">
	import Circle from "../lib/Circle.svelte";
    import { fly } from 'svelte/transition';
	import { onMount } from "svelte";

    let state: "name" | "play" | "greet" | "none" = "none"

    onMount(() => {
        state = "name"
    })

    function autofocus(elem: HTMLInputElement) {
        elem.focus()
    }

    let name = ""
</script>

{#if state == "name"}
    <main 
        in:fly="{{ y: -200, duration: 2000 }}"
        out:fly="{{ x: -600, duration: 1000 }}"
    >
        <h1>Hello there. What's your name?</h1>
        <input use:autofocus bind:value={name} placeholder="Enter Name" />
        <button 
            style:visibility={name.length > 0 ? "visible" : "hidden"}
            on:click={() => state = "greet"}
        >Continue</button>
    </main>
{:else if state == "greet"}
    <main
        in:fly="{{ x: 200, duration: 2000 }}"
        out:fly="{{ x: -600, duration: 1000 }}"
    >
        <h1>Hello, {name}.</h1>
        <p>This is a breathing exercise. Follow the circle.</p>
        <p>When the circle expands, breathe in.</p>
        <p>When the circle contracts, breathe out.</p>
        <button on:click={() => state = "play"}>Continue</button>
    </main>
{:else if state == "play"}
    <main transition:fly="{{ y: 200, duration: 2000 }}">
        <Circle />
    </main>
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

    input {
        border: none;
        border-bottom: 1px solid black;
        font-size: 1.5rem;
        padding: 0.5rem;
        outline: none;
        text-align: center;
    }

    button {
        border: none;
        background-color: white;
        color: black;
        border: 1px solid black;
        font-size: 1.5rem;
        padding: 1rem;
        margin-top: 1rem;
        border-radius: 0.5rem;
        cursor: pointer;
    }

    button:hover {
        background-color: #eee;
    }
</style>