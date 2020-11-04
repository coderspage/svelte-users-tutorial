<script>
  import { users } from './data-users.js'
  export let key
  export let user
  let undo = false

  const deleteUser = () => {
    undo = true
    setTimeout( ()=>{
      if(undo){
        delete $users[key]
        $users = $users
        undo = false
      }
    }, 3000 )
  }
  const undoDeleteUser = () => {
    undo = false  
    
  }
</script>

<!-- ############################## -->

<style>
  .user{
    display: grid;
    grid-template-columns: 3fr 10fr 3fr;
    grid-gap: 10px;
  }
  input{
    width: 100%;
    border: 1px solid gray;
    outline: none;
    padding-left: 5px;
  }
  button{
    outline: none;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    padding: 5px;
  }
</style>

<!-- ############################## -->

<div class="user">
  <div>{key}</div>
  <input type="text" bind:value={user.name} autofocus>
  {#if !undo}
    <button on:click={deleteUser}>🗑️</button>
  {:else}
    <button on:click={undoDeleteUser}>Undo</button>
  {/if}
</div>


