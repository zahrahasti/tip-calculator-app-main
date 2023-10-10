<script lang="ts">
   import { createEventDispatcher } from "svelte";
  export let content,customInput=false;
   const dispatch=createEventDispatcher();
   function handleInput(){
    content=this.value;
    dispatch("getValue",{
       content
    })
   }
</script>

<div class="container"  class:custom-input={customInput} >
    <slot name="title"/>
    <div class="container-input">
         <label>
              <slot name="label"/>
         </label>
         <input 
          type="text" 
          on:input={handleInput}  
           class:custom-input={customInput}
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
        height:100%;
   }
 
   .container-input input{
    border-radius:4px;
    position:absolute;
    font-weight:700;
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
  input.text-center{
    text-align:center;
    padding:0 .5rem;
  }
  input.text-center::placeholder{
    color:var(--dark-green);

  }
  input:focus{
    border:1.5px solid var(--light-green);
    outline:none;
  }
 

</style>