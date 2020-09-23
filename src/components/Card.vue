<template>
<vs-card type="3">
    <template #title>
    <h3>{{title}}</h3>
    </template>
    <template #img>
        <img v-bind:src="image" class="img-fluid" />
    </template>
    <template #text>
    <p>Earth Date : {{des1}}</p>
    <p>Rover : {{des2}}</p>
    </template>
</vs-card>
</template>

<script>
export default {
    props: ['title','image','des1','des2']
};
</script>

<style>
</style>