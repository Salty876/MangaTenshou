<script>
        import {currentUser, pb} from '../../lib/pocketbase'
    let username
    let password
    let email


    async function login(){
        await pb.collection('users').authWithPassword(username,password)
    }

    async function signup(){
       
        
       const data = {
           username,
           password,
           passwordConfirm: password,
           name: username,
           email


       }

       const createdUser = await pb.collection('users').create(data)
       await pb.collection('users').requestVerification(email);

       await login()

     
   }  


   function logout(){
        pb.authStore.clear()
    }


</script>


{#if $currentUser}
    <p>Signed in as {$currentUser.username}</p>

{:else}

<form>
    <input
    placeholder="username"
    type="text"
    bind:value={username}
    >
    <input
    placeholder="email"
    type="text"
    bind:value={email}
    >
    <input
    placeholder="password"
    type="text"
    bind:value={password}
    >

    
    <button on:click={signup}>
        sign up
    </button>
</form>
{/if}





<button on:click={logout}>
    logout
</button>