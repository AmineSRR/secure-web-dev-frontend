<script>
    import { enhance } from '$app/forms';
    export let film;
    export let data
    let details = false
    function Edit() {
        if(edit) edit = false
        else edit = true
    }
    function Details() {
        if(details) details = false
        else details = true
    }
    let edit = false


</script>
<style>
    .article-preview {
        border: 1px solid #ccc;
        border-radius: 5px;
        margin-bottom: 20px;
        padding: 20px;
        position: relative;
    }

    .article-preview button {
        background-color: #0084ff;
        border: none;
        border-radius: 5px;
        color: #fff;
        cursor: pointer;
        font-weight: bold;
        padding: 10px 20px;
        position: absolute;
        right: 20px;
        top: 20px;
        text-transform: uppercase;
    }

    .article-preview p {
        margin: 0 0 10px;
        font-size: 16px;
    }

    .article-preview p:first-of-type {
        font-weight: bold;
        margin-top: 10px;
    }

    .article-preview p span {
        color: #999;
        font-size: 12px;
        margin-left: 10px;
    }
</style>
<div class="article-preview">
    <button on:click={Details}>Details</button>
    {#if details}
        <p>Type of movie : <span>{film.filmType}</span></p>
        <p>Name of producer : <span>{film.filmProducerName}</span></p>
        <p>End date : <span>{film.endDate}</span></p>
        <p>Number district : <span>{film.district}</span></p>
        <p>Geolocation : <span>{film.geolocation.coordinates} {film.geolocation.type}</span></p>
        <p>Source location ID : <span>{film.sourceLocationId}</span></p>
        <p>Director : <span>{film.filmDirectorName}</span></p>
        <p>Address : <span>{film.address}</span></p>
        <p>Start date : <span>{film.startDate}</span></p>
        <p>Year : <span>{film.year}</span></p>
    {/if}

    {#if data.user.role === 'admin'}
    <button on:click={Edit}>
        EDIT
    </button>
        {/if}
    {#if edit}
        <form use:enhance method="POST" action="?/editLocation&id={film._id}" >
            <p>Type of movie : <textarea  name="filmType" placeholder="filmType" rows="1" >{film.filmType}</textarea></p>
            <p>Name of producer : <textarea  name="filmProducerName" placeholder="filmProducerName" rows="1" >{film.filmProducerName}</textarea></p>
            <p>End date : <textarea  name="endDate" placeholder="endDate" rows="1" >{film.endDate}</textarea></p>
            <p>Name of movie : <textarea  name="filmName" placeholder="filmName" rows="1" >{film.filmName}</textarea></p>
            <p>District : <textarea  name="district" placeholder="district" rows="1" >{film.district}</textarea></p>
            <p>Lattitude : <textarea  name="lattitute" placeholder="lattitude" rows="1" >{film.geolocation.coordinates[0]}</textarea></p>
            <p>Longitude : <textarea  name="longitude" placeholder="longitude" rows="1" >{film.geolocation.coordinates[1]}</textarea></p>
            <p>Source location ID : <textarea  name="sourceLocationId" placeholder="sourceLocationId" rows="1" >{film.sourceLocationId}</textarea></p>
            <p>Director : <textarea  name="filmDirectorName" placeholder="filmDirectorName" rows="1" >{film.filmDirectorName}</textarea></p>
            <p>Adress : <textarea  name="address" placeholder="address" rows="1" >{film.address}</textarea></p>
            <p>Start date : <textarea  name="startDate" placeholder="startDate" rows="1" >{film.startDate}</textarea></p>
            <p>Year : <textarea  name="year" placeholder="year" rows="1" >{film.year}</textarea></p>
            <button>
                EDIT
            </button>
        </form>
    {/if}
</div>

