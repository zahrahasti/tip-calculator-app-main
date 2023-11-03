 <script lang="ts">
  import { createEventDispatcher } from "svelte";
   import Box from "./Box.svelte";
  let clicked=false;
  const contents=[5,10,15,25,50]
  const dispatch=createEventDispatcher()
  function handleClick(e:Event){
    e.preventDefault();
    const boxes=[...document.querySelectorAll("[data-content]")] as HTMLElement[];
    boxes.forEach(box=>{
      box.style.backgroundColor="hsl(183, 100%, 15%)"
    })
    const btn= e.currentTarget as HTMLButtonElement;
    btn.style.backgroundColor="hsl(172, 67%, 45%)";
    const content:number=+this.dataset.content;
     dispatch("handleVal",{
      content
     })
}
 
 </script>

<div class="container">
    <h3>Select Tip %</h3>
    <div class="container-box">
     {#each contents as content}
     <Box {content} {clicked} on:click={handleClick}>
        <p slot="content">{content}%</p>
     </Box>
     {/each}
     <slot name="input" />
    </div>
    
</div>

<style>
    .container{
        margin-top:2rem;

    }
    h3{
        margin-bottom:1rem;
    }
.container-box{
    display: grid;
    gap: 1rem;
    grid-template-columns:repeat(3,1fr);
}
input.text-center{
    text-align:center;
    padding:0 .5rem;
  }
  input.text-center::placeholder{
    color:var(--dark-green);
  }
 @media (max-width:700px){
  .container-box{
    grid-template-columns:repeat(2,1fr);
  }
 }
</style>