<!-- <a href="/login">login</a>
<a href="/signUp">sign up</a>
<a href="/">Home</a>
<a href="/user/profile">profile</a> -->
<script>

    import {currentUser, pb} from '../lib/pocketbase'
    import { logout } from '../lib/authFuncs'
 
    let searchValue
    let searchBarStatus = false



    

</script>


<nav class='nav'>
    <div class="leftSide" >

    <!-- Where the sandwich menu goes -->
    <h1>MangaTenshou</h1>
    <!-- Where the logo goes -->
    </div>

    <div class="rightSide" >
        <div class='searchContainer'>
            <input
                class="searchbar"
                type="text"
                placeholder="Search"
                bind:value={searchValue}
          
            >
            <button class='searchButton'>
                <svg  xmlns="http://www.w3.org/2000/svg"  width="24"  height="24"  viewBox="0 0 24 24"  fill="none"  stroke="white"  stroke-width="2"  stroke-linecap="round"  stroke-linejoin="round"  class="icon icon-tabler icons-tabler-outline icon-tabler-search"><path stroke="none" d="M0 0h24v24H0z" fill="none"/>
                    <path d="M10 10m-7 0a7 7 0 1 0 14 0a7 7 0 1 0 -14 0" />
                    <path d="M21 21l-6 -6"/>
                </svg>            
            </button>
        </div>

        {#if $currentUser}
            <div class="dropdown">
                <a href="/user/profile">
                    <img class='profilePicture' src="http://127.0.0.1:8090/api/files/users/{$currentUser.id}/{$currentUser.avatar}?thumb=50x50" alt="pfp">
                </a>
                <div class='dropdownContent'>
                   <div class="nameAndPfp">
                    <img class='profilePicture' src="http://127.0.0.1:8090/api/files/users/{$currentUser.id}/{$currentUser.avatar}?thumb=50x50" alt="pfp">
                    <h3>{$currentUser.username}</h3>
                   </div>

                   <hr>

                   <ul>
                        <li>
                            <a href="/user/profile">Profile</a>
                        </li>

                        <li>
                            <a href="/user/readlist">My list</a>
                        </li>

                        <li>
                            <a href="/user/settings">Settings</a>
                        </li>
                        <hr>
                        <button class="logOut" on:click={logout}>
                            <svg  xmlns="http://www.w3.org/2000/svg"  width="24"  height="24"  viewBox="0 0 24 24"  fill="none"  stroke="currentColor"  stroke-width="2"  stroke-linecap="round"  stroke-linejoin="round"  class="icon icon-tabler icons-tabler-outline icon-tabler-logout-2"><path stroke="none" d="M0 0h24v24H0z" fill="none"/>
                                <path d="M10 8v-2a2 2 0 0 1 2 -2h7a2 2 0 0 1 2 2v12a2 2 0 0 1 -2 2h-7a2 2 0 0 1 -2 -2v-2" />
                                <path d="M15 12h-12l3 -3" />
                                <path d="M6 15l-3 -3" />
                            </svg>
                            Sign Out
                           </button>
                   </ul>
                
              
                </div>
            </div>

        {:else}

        <div class="dropdown">
            <a href="/">
                <img class='profilePicture' src="https://placehold.co/50" alt="pfp">
            </a>
            <div class='dropdownContent' id="guest">
               <div class="nameAndPfp">
                <img class='profilePicture' src="https://placehold.co/50" alt="guest pfp">
                <h3>Guest</h3>
               </div>

               <hr>

            
                  <div class="buttonBox">
                    <a href="/login" class="authLinks" data-sveltekit-reload>
                        <button class="logOrRegister" >
                            <svg  xmlns="http://www.w3.org/2000/svg"  width="24"  height="24"  viewBox="0 0 24 24"  fill="none"  stroke="currentColor"  stroke-width="2"  stroke-linecap="round"  stroke-linejoin="round"  class="icon icon-tabler icons-tabler-outline icon-tabler-logout-2"><path stroke="none" d="M0 0h24v24H0z" fill="none"/>
                                <path d="M10 8v-2a2 2 0 0 1 2 -2h7a2 2 0 0 1 2 2v12a2 2 0 0 1 -2 2h-7a2 2 0 0 1 -2 -2v-2" />
                                <path d="M15 12h-12l3 -3" />
                                <path d="M6 15l-3 -3" />
                            </svg>
                            Log In
                        </button>
                    </a>

                       <a href="/register" class="authLinks" data-sveltekit-reload>
                        <button class="logOrRegister" id='register' >
                            <svg  xmlns="http://www.w3.org/2000/svg"  width="24"  height="24"  viewBox="0 0 24 24"  fill="none"  stroke="currentColor"  stroke-width="2"  stroke-linecap="round"  stroke-linejoin="round"  class="icon icon-tabler icons-tabler-outline icon-tabler-logout-2"><path stroke="none" d="M0 0h24v24H0z" fill="none"/>
                                <path d="M10 8v-2a2 2 0 0 1 2 -2h7a2 2 0 0 1 2 2v12a2 2 0 0 1 -2 2h-7a2 2 0 0 1 -2 -2v-2" />
                                <path d="M15 12h-12l3 -3" />
                                <path d="M6 15l-3 -3" />
                            </svg>
                            Register
                        </button>
                        </a>

                    </div>
    
            
          
            </div>
        </div>
            
        {/if}
    </div>

</nav>



<slot class='slot'></slot>

{#if $currentUser}
    <h1>logged</h1>
{:else}
    <h1>Guest</h1>
{/if}

<style>
    :global(body){
        margin: 0;
        background-color: #09090B;

        }
    nav{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;

        width:  calc(100% - 6vw);
        height: 8vh;

        background-color: #27272A;

        
        padding-left: 3vw;
        padding-right: 3vw;

    }

    .searchButton{
        width: 2vw;
        background-color: #71717a;
        border: none;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 10px;

    }

    .rightSide{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        gap:2vw;
    }

    .searchContainer{
        width: 20vw;
        height: 4vh;
        background-color: #71717a;

        display: flex;
        flex-direction: row;
        border-radius: 10px;

        transition-property: width;
        transition-duration: 0.2s;
        transition-timing-function: ease-out;
        transition-delay: 0s;
        padding-right: 10px;

    }



    input{
        flex-grow: 2;
        outline: 1vh;
        outline-style: none;
        border: none;
        background-color: #71717a;
        border-radius: 20px;
        padding-left: 10px;

        color: white;
        font-weight: 600;


        
        }

    ::placeholder{
        color: white;
        opacity: 1;
        font-weight: 600;
    }



        .searchContainer:focus-within{
        outline: 0.2rem;
        width: 40vw;
        outline-style: solid;
        outline-color: #9333ea;
     
    }

    .profilePicture{
        border-radius:30px ;
        
    }

    .dropdown{
        display: inline-block;
        justify-content: center;
        margin: 1vw;
        
    }

    .dropdownContent{
        padding-top: 30px;
        display: none;
        min-width: 20vw;
        height: 50vh;
        background-color: #262626;

    
    }

    .dropdown:hover .dropdownContent{
        display: flex;
        flex-direction: column;
        align-items: center;
        position: absolute;
        right: 0;

    }

    .dropdown:hover :global(body){
        filter: blur(10px);
    }


    hr{
        width: 90%;
        padding: 0;
    }

    ul{
        width: 100%;
        height: 50%;
        padding: 0;

       
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    h3{
        color: white;
        font-weight: 700;
    }

    a{
        text-decoration: none;
        color: white;
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }

    .authLinks{
        width: 100%;
        height: 50%;
    }

    li{
        width: 100%;
        height: 20%;
        padding: 0;
        text-decoration: none;
        list-style: none;
  

        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }


    hr{
        color: white;
    }
    li:hover{
        background-color: #9333ea;
    }

    .logOut{
        width: 90%;
        height: 30%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        gap: 1vw;

        border-color:#9333ea;
        border-style: solid;
        border-radius: 6px;

        background-color: #9333ea;

        font-size: 1.25rem;
        color: white;
        font-weight: 700;
    }

    #guest{
        
        justify-content: space-between;
        gap: 10%;
     

        

    }

    .buttonBox{
        width: 100%;
        height: 70%;
        display: flex;
        flex-direction: column;
        align-items: center;

        gap: 2%;

    }

    .logOrRegister{
        width: 90%;
        height: 50%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        gap: 1vw;

        border-color:#9333ea;
        border-style: solid;
        border-radius: 6px;

        background-color: #9333ea;

        font-size: 1.25rem;
        color: white;
        font-weight: 700;
    }

    #register{
        background-color: #262626;
        border: none;

    }

    div:hover .dropdownContent:not(:hover){
        filter: blur(50%);
    }
</style>
