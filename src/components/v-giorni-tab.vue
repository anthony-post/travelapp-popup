<template>
    <div class="v-giorni-tab" @click="isVisibleBlock = !isVisibleBlock">
        <p>{{ title }}</p>
        <div v-show="isVisibleBlock">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
        </div>
    </div>
</template>

<script>
export default {
    name: 'v-giorni-tab',
    components: {},
    props: {},
    data() {
        return {
            title: 'Giorni',
            isVisibleBlock: true
        }
    }
}
</script>

<style>

    .v-giorni-tab {
        margin: $margin;
    }

</style>