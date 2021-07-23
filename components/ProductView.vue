<template>
    <div>
        <button class="btn btn-info float-right" @click="onNew">
            New Item
        </button>
        <h5>Product View</h5>
        <hr>
        <form action="" @submit.prevent="onSave">
            <b-form-group label="Brand:">
                <b-form-input v-model="merchandise.brand"></b-form-input>
            </b-form-group>
            <b-form-group label="Product:">
                <b-form-input v-model="merchandise.product"></b-form-input>
            </b-form-group>
            <b-form-group label="Description:">
                <b-form-input v-model="merchandise.description"></b-form-input>
            </b-form-group>
            <b-form-group label="Price:">
                <b-form-input v-model="merchandise.price"></b-form-input>
            </b-form-group>
            <b-form-group label="No. of Stock:">
                <b-form-input v-model="merchandise.quantity"></b-form-input>
            </b-form-group>
            <b-form-group>
               <button class="btn btn-primary" type="submit">Save Changes</button>
                <button class="btn btn-danger" type="button" @click="onDelete" v-if="merchandise.id">Delete</button>
            </b-form-group>
        </form>
    </div>
</template>
<script>
export default {
    props: {
        merchandise: {}
    },
    methods: {
        async onSave() {
            try {
                if(!this.merchandise.id) {
                    await this.$axios.post('https://lentrix.tk/lmd/api/merchandises', this.merchandise)
                }else {
                    await this.$axios.put('https://lentrix.tk/lmd/api/merchandises/'+this.merchandise.id, this.merchandise)
                }
                this.$emit('saved');
            }catch(err) {
                alert(err.response.data.message)
            }
        },
        onNew() {
            this.$emit('newItem')
        },
        async onDelete() {
            try {
                this.$axios.delete('https://lentrix.tk/lmd/api/merchandises/'+this.merchandise.id)
                this.$emit('deleted')
            }catch(err) {
                alert(err.response.data.message)
            }
        }
    }
}
</script>