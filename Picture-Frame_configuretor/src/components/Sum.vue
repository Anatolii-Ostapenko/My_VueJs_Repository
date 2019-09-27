<template>
    <div class="sum">
        <p>Стоимость: <span class="sum-val">{{favoritesList.sum != null ? favoritesList.sum : 0 }}</span><span>грн</span></p>
    </div>
</template>
<script>
export default {
    props:['favoritesList'],
    data() {
        return {
            sum: 0
        }
    },
    
    computed: {
        /* double(){
            return this.favoritesList.sum
        } */
    },

}
</script>