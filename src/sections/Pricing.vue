<script>
import { NCard } from 'naive-ui'
import Button from '../components/Button.vue';

export default {
    components: { NCard, Button }
}
</script>

<template>
    <h1 class="header">PRICING</h1>
    <div class="grid">
        <NCard title="Standard Composition/Production">
            <Button style="float: right">Order Now</Button>
        </NCard>
        <NCard title="Advanced Composition/Production">
            <Button style="float: right">Order Now</Button>
        </NCard>
        <NCard title="Sound Designing">
            <Button style="float: right">Order Now</Button>
        </NCard>
        <NCard title="Mixing">
            <Button style="float: right">Order Now</Button>
        </NCard>
    </div>
</template>


<style scoped>
.header {
    font-size: xx-large;
    font-weight: bold;
    text-align: center;
}

.grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 10px;
    padding: 10px;
}

@media only screen and (max-width: 600px) {
    .grid {
        grid-template-columns: repeat(1, 1fr);
    }
}
</style>