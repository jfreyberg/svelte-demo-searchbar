<script>
    import { onMount, onDestroy } from 'svelte';

    let element;
    let interval;

    let colors = [
        "#3B3561",
        "#F5B700",
        "#DC0073",
        "#008BF8"
    ];

    function setRandomColor(){
        let randomColor = colors[Math.floor(Math.random() * colors.length)];
        element.style.color = randomColor;
    }

    function startColorChange(){
        interval = setInterval(() => {
            setRandomColor();
        }, 5000);
    }

    function stopColorChange(){
        clearInterval(interval);
        interval = null;
    }


    function toggleColorChange(){
        if(interval){
            stopColorChange();
            return;
        }
        startColorChange();
    }

    onMount(() => {
        setRandomColor();
        //startColorChange();
    });

    
    onDestroy(() => {
        clearInterval(interval);
    });

</script>

<h1 class="text-6xl font-extrabold text-white transition-colors duration-1000 cursor-pointer" bind:this={element} on:click={()=> 
setRandomColor()}>DemoSearch</h1>