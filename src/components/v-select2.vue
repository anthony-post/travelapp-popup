<template>
    <div class="v-select">
        <p 
            class="v-select-title"
            @click="areOptionsVisible = !areOptionsVisible">
                <span>alle</span>
                {{ selected2 }}
                <svg width="8" height="5" viewBox="0 0 8 5" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M1.2021 5.45512e-07L4 2.69005L6.7979 9.64647e-08L8 1.15552L4 5L1.10052e-07 1.15552L1.2021 5.45512e-07Z" fill="#979797"/>
                </svg>
        </p>
        <div 
            class="v-select-options"
            v-if="areOptionsVisible">
            <p
                v-for="option2 in options2"
                :key="option2.value"
                @click="selectOption2(option2)">
                {{ option2.name }}
            </p>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'v-select2',
        props: {
            options2: {
                type: Array,
                default() {
                    return []
                }
            },
            selected2: {
                type: String,
                default: ''
            }
        },
        data() {
            return {
                areOptionsVisible: false
            }
        },
        methods: {
            selectOption2(option2) {
                // console.log(option);
                this.$emit('select2', option2);
                this.areOptionsVisible = false;
            },
            hideSelect() {
                this.areOptionsVisible = false;
            }
        },
        mounted() {
            document.addEventListener('click', this.hideSelect.bind(this), true);
        },
        beforeDestroy() {
            document.removeEventListener('click', this.hideSelect);
        }
    }
</script>