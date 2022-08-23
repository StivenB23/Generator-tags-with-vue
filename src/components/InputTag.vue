<script>
export default {
    data() {
        return {
            currentValue: "",
            tags: []
        }
    },
    methods:{
        handleKeyDown(){
            if(this.currentValue !==""){
                const exits = this.tags.some(item => item ==this.currentValue);
                if(!exits){
                    this.tags.push(this.currentValue)
                    this.currentValue='';
                }
            }
        },
        brose(){
             if(this.currentValue ==""){
                this.tags.pop()
             }
        }
        ,
        deleteTag(tag){
            this.tags.splice(tag, 1)
        }
    }
}
</script>
<template>
    <div class="container"> 
        <h2 class="m-4 text-center">Generator tags</h2>
        <label>Name tag: </label>
    <input class="form-control" type="text" v-model="currentValue" v-on:keyup.enter="handleKeyDown" v-on:keyup.backspace="brose" />
    <div class="d-inline-block">
        <div class="d-flex p-2">
            <div class="d-flex mx-3 fs-2 p-2 alert alert-light shadow-sm" v-for="(tag, index) of tags" :key="index" >
                {{tag}} <button class=" mx-2 btn fs-4 text-danger btn-sm h-1" @click="deleteTag(index)">X</button>
            </div>
        </div>
    </div>
    </div>
    
</template>
<style scoped>
</style>