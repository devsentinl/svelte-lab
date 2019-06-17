<script>
    import {createEventDispatcher} from 'svelte'
    let dispatch=createEventDispatcher()
    function myCustom(){
        dispatch('changename')
    }
</script>

<style>
.btn-std{
    margin: 0;
    padding: .5rem;
    border-radius: .5rem;
    background-color: #5CB130;
    color: white;
    border: none;
    width: 100%;
    font-size: 12px;
    cursor: pointer;
}
.btn-std:hover{
    background-color: #555;
    color:white;
}

</style>

<div  class="center">
    <button class="btn-std" on:click={myCustom} >
    Agregar método de pago
    </button>
</div>
