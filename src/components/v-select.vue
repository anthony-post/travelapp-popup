<template>
    <div class="v-select">
        <p 
            class="v-select-title v-text"
            @click="areOptionsVisible = !areOptionsVisible">
                <span>dalle</span>
                {{ selected }}
                <svg width="8" height="5" viewBox="0 0 8 5" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M1.2021 5.45512e-07L4 2.69005L6.7979 9.64647e-08L8 1.15552L4 5L1.10052e-07 1.15552L1.2021 5.45512e-07Z" fill="#979797"/>
                </svg>
        </p>
        <div 
            class="v-select-options"
            v-if="areOptionsVisible">
            <p
                v-for="option in options"
                :key="option.value"
                @click="selectOption(option)">
                {{ option.name }}
            </p>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'v-select',
        props: {
            options: {
                type: Array,
                default() {
                    return []
                }
            },
            selected: {
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
            selectOption(option) {
                // console.log(option);
                this.$emit('select', option);
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
