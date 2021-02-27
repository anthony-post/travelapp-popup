<template>
    <div class="v-indata-tab" @click="isVisibleBlock = !isVisibleBlock">
        <p>{{ title }}</p>
        <div v-show="isVisibleBlock">
           <select name="" id="">
               <option value="">first</option>
               <option value="">second</option>
               <option value="">third</option>
           </select>
        </div>
    </div>
</template>

<script>
export default {
    name: 'v-indata-tab',
    components: {},
    props: {},
    data() {
        return {
            title: 'In data',
            isVisibleBlock: false
        }
    }
}
</script>

<style>

</style>