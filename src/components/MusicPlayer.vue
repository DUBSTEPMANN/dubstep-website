<template id="music-player">
    <div style="display: grid; grid-template-columns: min-content auto;">

        <div @click="togglePlayState()" class="song-cover" :style="`background-image: url('${track.cover}');`"
            :class="{small: !(track.cover)}">
            <div class="controls">
                <PlayIcon v-if="!playing"></PlayIcon>
                <PauseIcon v-if="playing"></PauseIcon>
            </div>
        </div>
        <div style="display: grid; grid-template-rows: auto min-content;">
            <div class="trackname">
                {{ track.name }}
            </div>
            <div style="background: black;" ref="progressbar">
                <div style="height:40px; transition: width 0.1s linear; background: var(--accent-foreground);"
                    :style="`width:${this.progressPercent}%`"></div>
            </div>
        </div>

        <audio ref="audio">
            <source :src="track.source" :type="this.type">
        </audio>

    </div>
</template>

<script>
import PlayIcon from 'vue-material-design-icons/Play.vue'
import PauseIcon from 'vue-material-design-icons/Pause.vue'

export default {
    name: 'MusicPlayer',
    components: {
        PlayIcon,
        PauseIcon
    },
    props: [
        'name',
        'source',
        'cover',
        'type'
    ],
    methods: {
        togglePlayState() {
            if (this.$refs.audio.paused) {
                this.$refs.audio.play()
                this.playing = true
            } else {
                this.$refs.audio.pause()
                this.playing = false
            }
        }
    },
    data() {
        return {
            playing: false,
            progress: 0, // in ms
            progressPercent: 0,
            track: {
                name: '',
                source: '',
                cover: ''
            }
        }
    },
    mounted() {
        this.$refs.audio.addEventListener('timeupdate', () => {
            this.progress = this.$refs.audio.currentTime
            this.progressPercent = this.progress / this.$refs.audio.duration * 100
        })

        this.$refs.audio.addEventListener('ended', () => {
            this.progress = 0
            this.progressPercent = 0
            this.playing = false
        })

        this.$refs.progressbar.onclick = (e) => {
            const rect = e.currentTarget.getBoundingClientRect()
            //calculate progress
            const progress = (e.clientX - rect.left) / rect.width
            this.$refs.audio.currentTime = progress * this.$refs.audio.duration
        }

        this.track.name = this.name
        this.track.source = this.source
        this.track.cover = this.cover
    }
}
</script>

<style scoped>
.trackname {
    height: auto;
    vertical-align: bottom;
    padding: 10px;
    font-size: x-large;
    font-weight: bold;
}

@media only screen and (max-width: 600px) {
    .trackname {
        font-size: large;
    }
}

@media only screen and (max-width: 400px) {
    .trackname {
        font-size: medium;
    }
}

.song-cover {
    background-color: none;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    width: 96px;
    height: 98px;
}

.song-cover.small {
    background-color: var(--accent-foreground);
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    width: 64px;
    height: 98px;
}

.controls {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.1);
    transition: background-color 0.1s linear;
}

.controls:hover {
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    cursor: pointer;
}
</style>