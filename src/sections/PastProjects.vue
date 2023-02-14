<script>
import { NCard, NDrawer, NDrawerContent } from 'naive-ui'
import MusicPlayer from '../components/MusicPlayer.vue'
import Button from '../components/Button.vue'
import musicList from '../assets/audio-list'

export default {
    components: { MusicPlayer, NCard, NDrawer, Button, NDrawerContent },
    data: function () {
        return {
            active: false,
            musicList: musicList,
        }
    }
}
</script>

<template>
    <h1 class="header">PAST PRODUCTION</h1>
    <NCard embedded>
        <music-player name="Same thing" source="../audio/Samething(EDM production).mp3" cover="../cover/samething.png"
        type="audio/mp3"></music-player>
        <music-player name="Rain(Sound track production)" source="../audio/Rain(Sound track production).mp3" cover="../cover/rain.png"
        type="audio/wav"></music-player>
    </NCard>
    <Button class="center" @click="active = true">SEE ALL</Button>
    <NDrawer v-model:show="active" placement="bottom" height="90%">
        <NDrawerContent title="Past Projects" closable>
            <div v-for="music in musicList">
                <music-player :name="music.name" :source="`/audio/${music.fileName}`"
                :cover="music.cover ? `/cover/${music.cover}` : undefined"></music-player>
            </div>
        </NDrawerContent>
    </NDrawer>
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

.center {
    margin: auto;
    display: block
}
</style>