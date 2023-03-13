<script lang="ts">
    import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';
	import { onMount } from "svelte";

	const radius = tweened(0, {
		duration: 4000,
		easing: cubicOut
	});

    let dimension = 300;

    async function setAndWait(time: number, type: "expand" | "contract") {
        if (type == "expand") {
            radius.set(dimension)
        } else {
            radius.set(0)
        }

        await new Promise(resolve => setTimeout(resolve, time))
    }

    onMount(async () => {
        await setAndWait(2000, "expand")
        await setAndWait(5000, "contract")
        await setAndWait(5000, "expand")
        await setAndWait(5000, "contract")
        await setAndWait(5000, "expand")
    })
</script>

<div class="background-circle" style="width: {dimension}px; height: {dimension}px;"></div>
<div class="foreground-circle" style="width: {$radius}px; height: {$radius}px;"></div>

<style>
    div {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        border-radius: 50%;
    }

    .foreground-circle {
        background-color: rgba(0, 0, 255, 0.5);
    }

    .background-circle {
        background-color: rgba(0, 0, 255, 0.1);
    }
</style>