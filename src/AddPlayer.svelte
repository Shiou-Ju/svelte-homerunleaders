<script>
  import { createEventDispatcher  } from "svelte";
   const dispatch = createEventDispatcher();

   let player = {
    name:'',
    hrs: 0,
  }

  const onSubmit = (event)=>{
    event.preventDefault();
    dispatch('addplayer',player);
    // reset player
    player = {
      name : '',
      hrs: 0,
    }
  }
</script>

<form on:submit="{onSubmit}" class="grid-3">
  <input type="text" placeholder="球員姓名" bind:value="{player.name}">
  <input type="number" placeholder="全壘打數" bind:value="{player.hrs}">
  <input type="submit" class="btn btn-primary" value="新增球員" >

</form>