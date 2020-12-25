<template>
    <div :class="`number-${value.length > 2 ? 4 : 2}${small ? '-small' : ''}`">
        <app-digit v-for="(digit, i) in digits" :key="`${id}-${i}`" :value="digit" :small="small" />
    </div>
</template>

<script>
import AppDigit from '@/components/AppDigit.vue';

export default {
    name: 'AppNumber',
    props: {
        value: String,
        small: Boolean,
    },
    components: {
        AppDigit,
    },
    computed: {
        digits() {
            return (this.value ?? '0')
                .toString()
                .split('')
                .map((x) => parseInt(x));
        },
    },
    data: () => ({
        id: `number-holder-${Number.MAX_SAFE_INTEGER * Math.random()}`,
    }),
};
</script>
