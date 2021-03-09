<template>
    <div class="v-main-container">
        <p class="v-title">{{ title }}</p>
        <p class="v-text v-text-position-left">{{ description }}</p>

        <v-tabs></v-tabs>

        <div class="v-sub-container">
            <p class="v-text">{{ departure }}</p>

            <div class="v-select-wrapper">
                <!--@select="optionSelect" ловим выбранную опцию из дочернего компонента v-select-time 
                    :options='options' - связываем дочерний компонент с родителем
                    :selected="selected" - связываем дочерний компонент с родителем
                    :pretext="pretext" - связываем дочерний компонент с родителем
                -->
                <v-select-time
                    :pretext="pretext"
                    :options="options"
                    @select="optionSelect"
                    :selected="selected">
                </v-select-time>
                <v-select-time
                    :pretext="pretext2"
                    :options="options2"
                    @select="optionSelect2"
                    :selected="selected2">
                </v-select-time>

                <!-- <v-select
                    :options='options'
                    @select="optionSelect"
                    :selected="selected">
                </v-select> -->
                <!-- <v-select2
                    :options2='options2'
                    @select2="optionSelect2"
                    :selected2="selected2">
                </v-select2> -->
            </div>

            <p class="v-text">{{ place }}</p>

            <iframe 
                class="map"
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2572.298328369436!2d7.626925715417495!3d45.93901557910936!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x4788ccc312c35a99%3A0x6c0015381a86b4a1!2sSentiero%20Partenza%20da%20Cervinia%20per%20Chiesetta%20BTG%20Monte%20Cervino%20per%20Rif.%20Oriond%C3%A9%20a%20Croce%20Carrel%20Segnavia%2013EE!5e1!3m2!1sen!2sru!4v1613893599403!5m2!1sen!2sru" 
                width="100%" height="95" style="border:0;" allowfullscreen="" loading="lazy">
            </iframe>

            <button class="button btn-add">&plus; Aggiungi</button>

            <button class="button btn-done">Done</button>
        </div>

        <div class="home-indicator"></div>
    </div>
</template>

<script>
    import VTabs from './v-tabs.vue'
    import VSelectTime from './v-select-time.vue'
    // import vSelect from './v-select'
    // import vSelect2 from './v-select2'

    export default {
        name: 'v-main-container',
        components: {
            VTabs,
            VSelectTime
            // vSelect,
            // vSelect2
        },
        props: {},
        data() {
            return {
                title: 'Giorni, luoghi e orari',
                description: 'Quando si svolge il servizio',
                departure: 'Orario di partenza da Cervinia o incontro',
                place: 'Luogo di partenza o incontro con i clienti',

                pretext: 'dalle', //строка - префикс ко времени для select dalle
                selected: '15:00', //строка - опция по-умолчанию для select dalle
                options: [
                    {name: '15:00', value: 1},
                    {name: '16:00', value: 2},
                    {name: '17:00', value: 3}
                ], //массив с объектами - список опций для select dalle

                pretext2: 'alle',
                selected2: '18:00',
                options2: [
                    {name: '18:00', value: 1},
                    {name: '19:00', value: 2},
                    {name: '20:00', value: 3}
                ]
            }
        },
        methods: {
            optionSelect(option) {
                this.selected = option.name; //записываем выбранную опцию в опцию по-умолчанию для select dalle
            },
            optionSelect2(option) {
                this.selected2 = option.name;
            }
        }
    }
</script>