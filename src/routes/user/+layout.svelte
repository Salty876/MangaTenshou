<script>
        import {currentUser, pb} from '../../lib/pocketbase'

</script>



{#if $currentUser}
<a href="/user/settings">settings</a>
<a href="/user/readlist">list</a>
<a href="/user/profile">profile</a>
<a href="/">Home</a>

<slot></slot>

{:else}
<p>Not logged in</p>
{/if}
