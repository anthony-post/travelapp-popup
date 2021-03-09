<template>
    <div class="v-select">
        <p 
            class="v-select-title v-text"
            @click="areOptionsVisible = !areOptionsVisible"> <!--делает видимым/скрытым список с опциями-->
                <span>{{ pretext }}</span>
                {{ selected }}
                <svg width="8" height="5" viewBox="0 0 8 5" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M1.2021 5.45512e-07L4 2.69005L6.7979 9.64647e-08L8 1.15552L4 5L1.10052e-07 1.15552L1.2021 5.45512e-07Z" fill="#979797"/>
                </svg>
        </p>
        <div 
            class="v-select-options"
            v-if="areOptionsVisible"> <!--по-умолчанию блок с опциями НЕ виден-->
            <p
                v-for="option in options"
                :key="option.value"
                @click="selectOption(option)"> <!--обработчик клика по опции из списка-->
                {{ option.name }}
            </p>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'v-select-time',
        props: {
            options: {
                type: Array, //для передачи опций из родителя
                default() {
                    return []
                }
            },
            selected: {
                type: String, //для передачи выбранного значения по-умолчанию из родителя
                default: ''
            },
            pretext: {
                type: String, //для передачи префикса из родителя
                default: ''
            }
        },
        data() {
            return {
                areOptionsVisible: false 
            }
        },
        methods: {
            selectOption(option) { //option - объект из массива options родителя
                // console.log(option);
                this.$emit('select', option); //проталкиваем выбранную опцию в родительский компонент
                this.areOptionsVisible = false; //делаем невидимым список с опциями
            },
            hideSelect() {
                this.areOptionsVisible = false; //делает невидимым список с опциями
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
