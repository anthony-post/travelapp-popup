<template>
    <div class="v-tabs">

        <ul class="v-tabs-list">
            <li class="tab" 
                v-for="(tab, index) in tabs" 
                :key="index"
                @click="selectedTab = tab" 
                :class="{ activeTab: selectedTab === tab }">
                {{ tab }}
            </li>
        </ul>

        <div 
            class="v-block-giorni"
            v-show="selectedTab === 'Giorni'"> <!--при выполнении условия v-show этот блок показывается-->

            <input type="checkbox" class="custom-checkbox day-lu" id="Lu" name="day" value="yes">
            <label for="Lu"></label>
            <input type="checkbox" class="custom-checkbox day-ma" id="Ma" name="day" value="yes">
            <label for="Ma"></label>
            <input type="checkbox" class="custom-checkbox day-me" id="Me" name="day" value="yes">
            <label for="Me"></label>
            <input type="checkbox" class="custom-checkbox day-gi" id="Gi" name="day" value="yes">
            <label for="Gi"></label>
            <input type="checkbox" class="custom-checkbox day-ve" id="Ve" name="day" value="yes">
            <label for="Ve"></label>
            <input type="checkbox" class="custom-checkbox day-sa" id="Sa" name="day" value="yes">
            <label for="Sa"></label>
            <input type="checkbox" class="custom-checkbox day-do" id="Do" name="day" value="yes">
            <label for="Do"></label>

            <!-- <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox">
            <input type="checkbox"> -->
        </div>

        <div 
            class="v-block-indata"
            v-show="selectedTab === 'In data'"> <!--при выполнении условия v-show блок показывается-->

            <p class="v-text v-text-position-indata">Seleziona la data dell'evento</p>

            <v-select-date
                :optionsDate='optionsDate'
                @selectDate="optionSelectDate"
                :selectedDate="selectedDate">
            </v-select-date>
        </div>

    </div>
</template>

<script>
    import VSelectDate from './v-select-date.vue'

    export default {
        name: 'v-tabs',
        components: {
            VSelectDate
            },
        props: {},
        data() {
            return {
                tabs: ['Giorni', 'In data'], //загаловки вкладок
                selectedTab: 'Giorni', //см. выше - по клику @click на вкладку в это свойство будет записываться значение tab с названием активной вкладки
                optionsDate: [
                    {name: '20.12.2020', value: 1},
                    {name: '21.12.2020', value: 2}
                ],
                selectedDate: '22.12.2020'
            }
        },
        methods: {
            optionSelectDate(optionDate) {
                this.selectedDate = optionDate.name;
            }
        }
    }
</script>
