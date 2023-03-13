<script lang="ts">
    import "../app.css" 
    import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

	const radius = tweened(0, {
		duration: 4000,
		easing: cubicOut
	});

    let dimension = 300;

    radius.set(dimension)
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