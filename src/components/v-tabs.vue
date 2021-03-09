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

            <ul class="checkbox-list"> <!--вывод checkbox через v-for-->
                <li 
                    class="checkbox-item"
                    v-for="classItem in classListDays" 
                    :key="classItem"> 
                    <input type="checkbox" :class="classItem" :id="classItem" name="day" value="yes">
                    <label :for="classItem"></label>
                </li>
            </ul>

            <!-- <input type="checkbox" class="custom-checkbox day-lu" id="Lu" name="day" value="yes">
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
            <label for="Do"></label> -->

        </div>

        <div 
            class="v-block-indata"
            v-show="selectedTab === 'In data'"> <!--при выполнении условия v-show блок показывается-->

            <p class="v-text v-text-position-indata">Seleziona la data dell'evento</p>

            <!-- <v-select-time
                :pretext="pretext3"
                :options='optionsDate'
                @select="optionSelectDate"
                :selected="selectedDate">
            </v-select-time> -->

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
    // import VSelectTime from './v-select-time.vue';

    export default {
        name: 'v-tabs',
        components: {
            VSelectDate
            // VSelectTime
            },
        props: {},
        data() {
            return {
                tabs: ['Giorni', 'In data'], //загаловки вкладок
                classListDays: ['custom-checkbox day-lu', 'custom-checkbox day-ma', 'custom-checkbox day-me', 'custom-checkbox day-gi', 'custom-checkbox day-ve', 'custom-checkbox day-sa', 'custom-checkbox day-do'],
                selectedTab: 'Giorni', //см. выше - по клику @click на вкладку в это свойство будет записываться значение tab с названием активной вкладки
                pretext3: '',
                optionsDate: [
                    {name: '22.12.2020', value: 1},
                    {name: '23.12.2020', value: 2},
                    {name: '24.12.2020', value: 2}
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
