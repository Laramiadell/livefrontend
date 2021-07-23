<template>
    <div>
        <NavBar />
        <div class="container">
        <div class="row">
            <div class="col-6">
                <h5>List of Products</h5>
                <ul class="list-group">
                    <li class="list-group-item list-group-item-action" v-for="merchandise in merchandises" :key="merchandise.id" @click="onSelected(merchandise)">
                        {{merchandise.product}} <span class="float-right">{{merchandise.price}}</span>
                    </li>
                    
                </ul>
            </div>
            <div class="col-4">
                <ProductView :merchandise="selectedMerchandise" @saved="onChanges" @newItem="onNew" @deleted="onChanges"/>
            </div>
        </div>
    </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            merchandises: [],
            selectedMerchandise: {}
        }
    },
    methods: {
        async getMyMerchandises() {
            await this.$axios.get('https://lentrix.tk/lmd/api/merchandises')
            .then((res)=>{
                if(res.status==200) {
                    this.merchandises = res.data
                }
            })
        },
        onChanges() {
            this.getMyMerchandises()
            this.selectedMerchandise = {}
        },
        onSelected(merchandise) {
            this.selectedMerchandise = merchandise
        },
        onNew() {
            this.selectedMerchandise = {}
        }
    },
    created() {
        this.getMyMerchandises()
    }
}
</script>
<style scoped>
.container{
    margin-top: 50px;
}
</style>