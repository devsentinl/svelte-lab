<script>
export let value;
export let name;
export let style;
</script>

<style>
.tarjeta{
    border-radius: .5rem;
    width: 100%;
    height: 100%;
    background-color: #CCB375;
    padding: 1rem;
    box-sizing: border-box;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 50px 1fr 1fr;
}
.tarjeta-visa{
    border-radius: .5rem;
    width: 100%;
    height: 100%;
    background-color: #7FB4E2;
    padding: 1rem;
    box-sizing: border-box;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 50px 1fr 1fr;
}
.span2{
        grid-column: span 2;
}
.img-logovisa{
    background-image: url(./img/visa.svg);
    background-repeat: no-repeat;
}
.img-logomastercard{
    background-image: url(./img/mastercard.svg);
    background-repeat: no-repeat;
}
.img-tarjeta{
background-image: url(./img/tarjeta.svg);
    background-repeat: no-repeat;
}
</style>

<div class="{value.substring(0,1)=="4"?"tarjeta-visa":"tarjeta"}" >
    <div class="img-tarjeta"></div>
    <div class="{value.substring(0,1)=="4"?"img-logovisa":"img-logomastercard"}"></div>
    <label for="" class="span2" >{value}</label>
    <label for="" class="span2">{name}</label>
</div>
