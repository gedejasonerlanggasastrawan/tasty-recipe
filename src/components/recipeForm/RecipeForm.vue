<script setup>
    import RecipeFormHeader from './RecipeFormHeader.vue';
    import RecipeFormBody from './RecipeFormBody.vue';

    defineProps({
        isEdit: { type: Boolean, default: false },
        detailData: { type: Object, default: () => ({}) },
    });
</script>


<template>
    <ul class="list-group">
        <recipe-form-header></recipe-form-header>
        <recipe-form-body :isEdit="isEdit" :detailData="detailData"></recipe-form-body>
    </ul>
</template>

