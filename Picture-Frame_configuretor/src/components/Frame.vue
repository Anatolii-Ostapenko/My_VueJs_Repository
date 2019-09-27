<template>
    <div class="frame">
        <div class="choice-field">
            <Tabs @selectTab="selectTab"/>
            <component :is="componentName" :pictureList="pictureList" @selectPicture='selectPicture'></component>
            <Sum :favoritesList='favoritesList'/>
        </div>
        <div class="result-field">
            <ChoiceResult :favoritesList='favoritesList' @nextStep='nextStep'/>
        </div>
    </div>
</template>

<script>
    import Tabs from './Tabs';
    import SelectPicture from './SelectPicture';
    import SelectFrame from './SelectFrame';
    import Sum from './Sum';
    import ChoiceResult from './ChoiceResult'
    
    export default {
        components:{
            Tabs,
            SelectPicture,
            SelectFrame,
            Sum,
            ChoiceResult
        },
        data() {
            return {
                page: 0,
                componentName: 'SelectPicture',
                pictureList: [
                    {id: 0, pictureUrl: require('@/assets/img/pics/01.jpg'), price: 500},
                    {id: 1, pictureUrl: require('@/assets/img/pics/02.jpg'), price: 750},
                    {id: 2, pictureUrl: require('@/assets/img/pics/03.jpg'), price: 600},
                    {id: 3, pictureUrl: require('@/assets/img/pics/04.jpg'), price: 990},
                    {id: 4, pictureUrl: require('@/assets/img/pics/05.jpg'), price: 1500},
                    {id: 5, pictureUrl: require('@/assets/img/pics/06.jpg'), price: 450},
                    {id: 6, pictureUrl: require('@/assets/img/pics/07.jpg'), price: 900},
                    {id: 7, pictureUrl: require('@/assets/img/pics/08.jpg'), price: 1800},
                    {id: 8, pictureUrl: require('@/assets/img/pics/09.jpg'), price: 1200},
                    {id: 9, pictureUrl: require('@/assets/img/pics/10.jpg'), price: 740},
                    {id: 10, pictureUrl: require('@/assets/img/pics/11.jpg'), price: 890}
                ],
                favoritesList: {
                    sum: null,
                    pictureNumber: null,
                    pictureUrl: '',
                    frameNamber: null,
                    frameUrl: null,
                    fingerprints: ''
                }
            }
        },
        methods: {
            nextStep(){
                this.page += 1;
                this.setPage(this.page)
            },
            setPage(){
                switch (this.page) {
                    case 1: 
                        this.componentName = 'SelectFrame'
                        break;
                    default:
                        this.componentName = 'SelectPicture'
                }
            },
            selectTab(index){
                this.setPage(index)
            },
            selectPicture(obj){
                this.favoritesList.sum = obj.price;
                this.favoritesList.pictureNumber = obj.id+1;
                this.favoritesList.pictureUrl = obj.pictureUrl
            } 
        },
        /* created() {
            this.setPage()
            alert(this.page)
        }  */
    }
    
</script>