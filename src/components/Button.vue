<template>
    <button class="button" :style="style">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: [
        'style'
    ]
}
</script>

<style scoped>
.button {
    background-color: var(--accent-foreground);
    padding: 10px;
    font-size: larger;
    border: none;
}

.button:hover {
    filter: brightness(1.2);
    cursor: pointer;
}

.button:active {
    filter: brightness(0.8);
    cursor: pointer;
}

.button:disabled {
    background-color: var(--accent-foreground-disabled);
    cursor: not-allowed;
}

</style>