<script>
export default {
    emits: ["onClickAutoComplete"],
    props: {
        searchAutoData: {
            type:String,
            required: true,  
        }
    }
    
}
</script>
<template>
    <li class="auto-complete-list" @click="$emit('onClickAutoComplete',searchAutoData)">
        <span><i class="fas fa-search"></i></span> {{ searchAutoData }}
    </li>
</template>
