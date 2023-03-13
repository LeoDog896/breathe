<script lang="ts">
    import "../app.css" 

    let dimension = 300;
</script>

<div class="background-circle" style="width: {dimension}px; height: {dimension}px;"></div>
<div class="foreground-circle"></div>

<style>
    div {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        border-radius: 50%;
    }

    .background-circle {
        background-color: rgba(0, 0, 255, 0.1);
    }
</style>