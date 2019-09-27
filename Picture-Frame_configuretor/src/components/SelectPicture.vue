<template>
    <div class="select-picture">
        <h3>Выберете изображение</h3>
        <p>Для начала выберите основу, саму картину, на которую вы и гости вашего праздника будете наносить отпечатки пальцев с пожеланиями</p>
        <div class="wrapp-picture">
            <div v-for="(pictue, index) in pictureList" class="picture-frame" :class="{'highlight': index == activeIndex}" :key="index" @click="selectPicture(pictue, index)">
                <img :src="pictue.pictureUrl" :alt="index">
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props:['pictureList'],
    data() {
        return {
           activeIndex: null
        }
    },
    methods:{
        selectPicture(pictue, index){
            this.activeIndex = index
            this.$emit('selectPicture', pictue)
        }
    }
}
</script>