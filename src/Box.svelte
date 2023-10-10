<script lang="ts">
  export let content;
  export let lightGreen=false,clicked=false;
</script>


<button type="button" data-content={content} on:click class:clicked={clicked} class:light-green={lightGreen}>
    <slot name="content" />
</button>

<style>
    button{
        border:1px solid hsl(183, 100%, 15%);
        cursor: pointer;
        background:hsl(183, 100%, 15%);
        color:hsl(189, 41%, 97%);
        font-size:1.2rem;
        border-radius:4px;
        width: 100%;
        padding:.5rem;
        text-align:center;
        transition:all .3s ease-in-out;
    }
    button:hover,button:focus{
        background: hsl(172, 67%, 45%);
        border:1px solid hsl(172, 67%, 45%);
        color:hsl(183, 100%, 15%);
    }
    button.light-green{
    border:none;
    color:var(--dark-green);
    background:var(--light-green);
  }
  button.clicked{
    background: hsl(172, 67%, 45%);
    border:1px solid hsl(172, 67%, 45%);
    color:hsl(183, 100%, 15%);
  }
  button.light-green:hover{
    background:var(--light-grayish-cyan);
  }
</style>