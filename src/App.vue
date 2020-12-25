<template>
    <div>
        <app-date :day="day" :month="month" :year="year" />
        <br />
        <app-time :hours="hours" :minutes="minutes" :seconds="seconds" />
    </div>
</template>

<script>
import AppDate from '@/components/AppDate.vue';
import AppTime from '@/components/AppTime.vue';

export default {
    name: 'App',
    components: {
        AppDate,
        AppTime,
    },
    methods: {
        fixedDigits(value, digits) {
            const number = parseInt(value ?? '0');
            return ('0' + number).slice(-digits);
        },
        recalculateState() {
            const now = new Date();

            this.day = this.fixedDigits(now.getDate(), 2);
            this.month = this.fixedDigits(
                this.calcFakeMonth(now.getMonth() + 1, now.getFullYear()),
                2,
            );
            this.year = this.fixedDigits(this.calcFateYear(now.getFullYear()), 4);

            this.seconds = this.fixedDigits(now.getSeconds(), 2);
            this.minutes = this.fixedDigits(now.getMinutes(), 2);
            this.hours = this.fixedDigits(now.getHours(), 2);
        },
        calcFakeMonth(realMonth, currYear) {
            if (currYear <= 2020) {
                return realMonth;
            }
            return realMonth + (currYear - 2020) * 12;
        },
        calcFateYear(currYear) {
            return currYear > 2020 ? 2020 : currYear;
        },
    },
    data: () => ({
        day: '0',
        month: '0',
        year: '0',
        hours: '0',
        minutes: '0',
        seconds: '0',
    }),
    mounted() {
        this.recalculateState();
        setInterval(this.recalculateState, 1000);
    },
};
</script>
