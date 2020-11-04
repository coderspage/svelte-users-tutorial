<script>
  import User from './User.svelte'
  import { users } from './data-users.js'
  const addUser = () => {
    const id = Math.floor(Math.random()*1000)
    let name = ""
    $users['ID'+id] = {id, name}
  }
</script>

<!-- ############################## -->

<style>
  #users{
    display: grid;
    grid-gap: 10px;
    padding: 10px;
  }
  button{
    height: 45px;
  }
</style>

<!-- ############################## -->

<div id="users">
  {#each Object.keys($users) as key}
    <User key={key} bind:user={$users[key]} />
  {/each}

  <button on:click={addUser}>Add User</button>

  <pre>
    {JSON.stringify($users, null, 2)}
  </pre>
</div>



