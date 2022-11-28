<script setup lang="ts">
import {PropType} from "@vue/runtime-core";

const { outline, color, size } = defineProps({
    size: {
        type: String as PropType<'medium' | 'large'>,
        default: 'medium',
    },

    outline: {
        type: Boolean,
        default: false,
    },

    color: {
        type: String as PropType<'red' | 'yellow'>,
        default: 'red',
    },
})

const classList: object = computed(() => ({
    '--is-outline': outline,
    '--is-solid': !outline,
    [`--${color}-color`]: color,
    [`--${size}-size`]: size,
}));
</script>

<template>
    <button :class="classList" class="UiButton">
        <slot/>
    </button>
</template>

<style lang="scss">
.UiButton {
    font-family: 'Proxima Nova Rg', sans-serif;
    cursor: pointer;
    transition: all .3s ease;
    border-width: 1px;
    border-color: transparent;
    border-style: solid;

    &.--medium-size {
        font-size: 14px;
        font-weight: bold;
        line-height: 16px;
        padding: 10px 40px;
        border-radius: 10px;
    }

    &.--large-size {
        font-size: 14px;
        line-height: 17px;
        padding: 20px 50px;
        font-weight: bold;
        border-radius: 10px;
    }

    &.--yellow-color {
        &.--is-outline {
            border-color: var(--yellow);
            color: var(--white);
            background-color: transparent;

            &:hover {
                background: var(--yellow);
            }
        }

        &.--is-solid {
            background: var(--yellow);

            &:hover {
                opacity: .8;
            }
        }
    }

    &.--red-color {
        &.--is-solid {
            background-color: var(--red);
            color: var(--white);

            &:hover {
                opacity: .8;
            }
        }
    }
}
</style>
