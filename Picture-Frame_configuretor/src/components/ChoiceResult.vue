<template>
    <div class="choice-result">
        
            <div class="title">
                <h3>Ваша картина</h3>
            </div>
            <div class="result">
                <p>Изображение: <span>{{favoritesList.pictureNumber != null ? 'Картинка №'+ favoritesList.pictureNumber : ''}}</span></p>
                <p>Рама:</p>
                <p>Отпечатки: </p>
                <div class="selection-result">
                    <img :src="favoritesList.pictureUrl" class="picture" />
                </div>
            </div>
            <button @click="nextStep()" class="nextStep">ДАЛЕЕ</button>
    </div>
</template>

<script>
export default {
    props:['favoritesList'],
    data(){
        return{

        }
    },
    methods: {
        nextStep(){
            this.$emit('nextStep');
        }
    },
}
</script>