<script>
export default {
    props: {
        searchAutoData: {
            type:String,
            required: true,  
        }
    }
}
</script>
<template>
<span><i class="fas fa-search"></i></span> {{ searchAutoData }}
</template>
