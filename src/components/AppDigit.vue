<template>
    <div :class="[`digit${suffix}`, `num-${value}`]">
        <div :class="['line', 'line-top', `line-horizontal${suffix}`]"></div>

        <div :class="['line', 'line-left-top', `line-vertical${suffix}`]"></div>
        <div :class="['line', 'line-right-top', `line-vertical${suffix}`]"></div>

        <div :class="['line', 'line-middle', `line-horizontal${suffix}`]"></div>

        <div :class="['line', 'line-left-bottom', `line-vertical${suffix}`]"></div>
        <div :class="['line', 'line-right-bottom', `line-vertical${suffix}`]"></div>

        <div :class="['line', 'line-bottom', `line-horizontal${suffix}`]"></div>
    </div>
</template>

<script>
export default {
    name: 'AppDigit',
    props: {
        value: Number,
        small: Boolean,
    },
    computed: {
        suffix() {
            return this.small ? '-small' : '';
        },
    },
};
</script>
