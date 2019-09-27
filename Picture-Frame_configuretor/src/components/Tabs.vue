<template>
    <div class="tabs">
        <div>
            <a href="#" v-for="(name, index) in tabsName" :key="index" @click="selectTab(index)">{{index+1}} {{name}}</a>
        </div>
    </div>
</template>
<script>
export default {
     data() {
        return {
            tabsName: ['Изображение', 'Рама', 'Заголовок', 'Цвет отпечатков']
        }
    },
    methods: {
        selectTab(index){
            this.$emit('selectTab', index);
        }
    },
}
</script>