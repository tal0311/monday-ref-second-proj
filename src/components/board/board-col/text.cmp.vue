<template>
    <div v-if="task" class="task-text">
        <div class="icon-dapulse-addbtn"></div>
        <div class="input-container">
        <form @submit.prevent="updateTask">
         <input v-model="text" class="location-input" type="text" :placeholder="textToDiaplay">    
         </form>
        </div>
    </div>
</template>
<script>
export default {
    emits:['updateTask'],
    name: ['textCmp'],
    props: {
        task: Object,
        row: Object,
    },

    data() {
        return {
            text: '',
        }
    },
    computed: {
        textToDiaplay(){
            if (!this.task.value) return ''
            return this.task.value
        }
    },
    methods:{
        updateTask() {
            let newCol = {type:this.task.type,value:this.text}
            let newData = {newCol,taskId:this.row.id,groupId:this.row.groupId}
            this.$emit('updateTask',newData)
            this.text = ''
        }
    }
}
</script>
