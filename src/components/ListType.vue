<template>
    <div>
        <ListDefault :elements-list = "elements" />
        <br>
        <h6>Created By Ing. Mario Alonso</h6>
    </div>
</template>

<script>

import ListDefault from '../partials/_ListDefault';

export default {
    components:{
        ListDefault
    },
    created() {
        this.findAll();
    },
    data(){
        return {
            elements: []
        };
    },
    methods: {
        findAll: function(){
            fetch('http://127.0.0.1:8000/api/type/' + this.$route.params.id + '/elements/?format=json')
                .then(res => res.json())
                .then(res => (this.elements = res));
        }
    },
    watch:{
        "$route.params.id": function(){
            console.log("Listado de Categorias");
            this.findAll();
        }
    }
};
</script>

<style>
    .box{
        border: 3px solid #CCC;
        margin: 5px 0 0 0;
    }
</style>