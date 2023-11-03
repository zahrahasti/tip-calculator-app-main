<script lang="ts">
  import { createEventDispatcher } from "svelte";
  export let content
 export let textPlaceholder;
   const dispatch=createEventDispatcher();
   function handleInput(){
    content=this.value;
    dispatch("getValue",{
       content
    })
   }
</script>

<div class="container" class:textPlaceholder={textPlaceholder} data-target="{textPlaceholder}">
    <slot name="title"/>
    <div class="container-input">
         <label>
              <slot name="label"/>
         </label>
         <input 
          type="number" 
          on:input={handleInput} 
          on:blur={handleInput}
          class:textPlaceholder
          placeholder="{textPlaceholder? `Custom` : "0"}"
          />
        
    </div>
</div>
 

<style>
     .container:first-child{
		 color:var(--dark-grayish)
	}
   
    .container-input{
        background:hsl(189, 41%, 97%);
        display: flex;
        position: relative;
        padding: 10px;
        align-items: center;
        justify-content:space-between;
        border-radius:4px;
        gap:.5rem;
        height:3rem;   
   }
 
   .container-input input{
    border-radius:4px;
    position:absolute;
    font-weight:500;
    font-size:1.2rem;
    text-align:right;
    background:transparent;
    border:1.5px solid hsl(189, 41%, 97%);
    outline:none;
    width: 100%;
    height: 100%;
    left:0;
    padding:0 1.5rem;
    color:var(--dark-green);
    font-weight: 700;
  }

  input.textPlaceholder{
    text-align: center;
    height: 100%;
  }
  input.textPlaceholder::placeholder{
    color:hsl(186, 14%, 43%);
  }
  input:focus{
    border:1.5px solid var(--light-green);
    outline:none;
  }
 

</style>