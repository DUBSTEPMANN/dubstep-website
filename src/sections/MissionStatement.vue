<script>
import { NCard } from 'naive-ui'

export default {
    components: { NCard }
}
</script>

<template>
    <h1 class="header">MISSION STATEMENT</h1>
    <div class="grid">
        <NCard embedded size="huge" title="To provide efficient, high standard, and affordable services.">
            <template #cover>
                <img src="../assets/mission-statement/1.png" alt="mission1" />
            </template>
        </NCard>
        <NCard embedded size="huge" title="To build, improve, and enhance, the sound of your imagination.">
            <template #cover>
                <img src="../assets/mission-statement/2.png" alt="mission1" />
            </template>
            
        </NCard>
        <NCard embedded size="huge" title="To be creative, imaginative, and innovative on every piece of work.">
            <template #cover>
                <img src="../assets/mission-statement/3.png" alt="mission1" />
            </template>
            
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
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
    padding: 10px;
}

@media only screen and (max-width: 600px) {
    .grid {
        grid-template-columns: repeat(1, 1fr);
    }
}
</style>