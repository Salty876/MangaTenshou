<script>
    import {currentUser, pb} from '../../../lib/pocketbase'
    import { onMount } from 'svelte';
    console.log($currentUser)
    let Ids = $currentUser.id
    let mangaList

    let listLength
    let listO = []


    onMount(async() => {
        mangaList = await pb.collection('mangaListEntry').getList(1, 50);
        listLength = (mangaList.items).length
        console.log(listLength)

        listO = Array.from(new Array(listLength), (x,i) => i)
        console.log(listO)
        console.log(mangaList.items);

        pb.collection('mangaListEntry').subscribe('*', function (e) {
            console.log(e.action);
            console.log(e.record);
})


})





    






    let mangaID
    let lastChapter
    let status

    async function addToList(){
        const data = {
        "mangaID": mangaID,
        "status": status,
        "lastChapter": lastChapter,
        "userID": Ids
};

        const record = await pb.collection('mangaListEntry').create(data);

    }

</script>


<form>
    <input
        type="text"
        placeholder="Manga ID"
        bind:value={mangaID}
    >

    <input
    placeholder="last chapter"
    bind:value={lastChapter}
    type="number"
    >

    <input
        type="text"
        placeholder="Status"
        bind:value={status}
    >


    <button on:click={addToList}>
        submit
    </button>
</form>


{#each listO as x}
    <div>
        <p>Manga ID: {mangaList.items[x].mangaID}</p>
        <p>Status: {mangaList.items[x].status}</p>
        <p>Last Chapter Read: {mangaList.items[x].lastChapter}</p>
    </div>
{/each}  

