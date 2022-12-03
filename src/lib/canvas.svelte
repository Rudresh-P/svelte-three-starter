<script>
    import { onMount, afterUpdate } from "svelte";
    import { page } from "$app/stores";
    import Sketch from "./app";

    let canvasElement;
    let sketch;

    let { route } = $page;

    afterUpdate(()=>{
        if(sketch){
            sketch.onRouteChange(route.id)
        }
    })

    onMount(()=>{
        sketch = new Sketch(canvasElement)
    })
</script>

<div class="canvas">
    <canvas bind:this={canvasElement}></canvas>
</div>