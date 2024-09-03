<script>
    import {currentUser, pb} from '../lib/pocketbase'

    let username
    let password







    function logout(){
        pb.authStore.clear()
    }

</script>


{#if $currentUser}
    <p>Signed in as {$currentUser.username}</p>

{:else}

    <p>Not logged in</p>
{/if}




<button on:click={logout}>
    logout
</button>