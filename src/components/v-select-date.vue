<template>
    <div class="v-select-date">
        <p 
            class="v-select-title-date"
            @click="areOptionsVisible = !areOptionsVisible">
            {{ selectedDate }}
            <svg width="8" height="5" viewBox="0 0 8 5" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M1.2021 5.45512e-07L4 2.69005L6.7979 9.64647e-08L8 1.15552L4 5L1.10052e-07 1.15552L1.2021 5.45512e-07Z" fill="#979797"/>
            </svg>
        </p>
        <div 
            class="v-select-options"
            v-if="areOptionsVisible">
            <p
                v-for="optionDate in optionsDate"
                :key="optionDate.value"
                @click="selectOptionDate(optionDate)">
                {{ optionDate.name }}
            </p>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'v-select-date',
        props: {
            optionsDate: {
                type: Array,
                default() {
                    return []
                }
            },
            selectedDate: {
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
            selectOptionDate(optionDate) {
                // console.log(option);
                this.$emit('selectDate', optionDate);
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
