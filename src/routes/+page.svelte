<script lang="ts">
    import "../app.css" 
    import { Canvas, Layer, t, type Render } from "svelte-canvas";

    let render: Render;
    $: render = ({ context, width, height }) => {
        context.beginPath();
        context.arc(width / 2, height / 2, Math.min(width, height) / 2, 0, 2 * Math.PI);
        context.fillStyle = "rgba(0, 0, 255, 0.1)";
        context.fill();
    };
</script>

<Canvas width={300} height={300} class="canvas">
    <Layer {render} />
</Canvas>

<style>
    :global(.canvas) {
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        position: absolute;
    }
</style>