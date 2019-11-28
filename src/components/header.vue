<template>
<div class="div-header">
    <slot></slot>
</div>
</template>

<script>
    export default {
        name: 'Header'
    }
</script>

<style>
h3{
    text-align:center;            
}

.div-header{
    border-bottom: 0.1px solid grey;
}
</style>