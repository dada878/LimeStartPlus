<template>
    <Transition>
        <div v-show="show" id="searchSuggestion" style="height: 270px;">
            <div v-for="item in suggests" :key="item">{{ item }}</div>
        </div>
    </Transition>
</template>
<script lang="ts">
import axios from 'axios';
import { defineComponent } from 'vue';
export default defineComponent({
    data() {
        return {
            suggests: []
        }
    },
    props: {
        show: {
            type: Boolean
        },
        searchBarValue: {
            type: String
        }
    },
    watch: {
        searchBarValue(after: string) {
            axios.get('http://localhost:8000/search.php?keyword=' + after).then((result) => {
                if (result.data.length > 0) this.suggests = result.data;
            });
        }
    }
})
</script>
<style lang="scss">
#searchSuggestion {
    z-index: 40;
    position: absolute;
    top: 255px;
    left: 50%;
    transform: translateX(-50%);
    width: 530px;
    max-width: 80%;
    height: auto;
    font-size: small;
    overflow-y: hidden;
    border-radius: 15px;
    transition: .25s;
    -webkit-backdrop-filter: blur(30px) saturate(1.25);
    backdrop-filter: blur(30px) saturate(1.25);
    
    & div {
        overflow: hidden;
        clear: both;
        height: 30px;
        padding-right: 10px;
        text-indent: 20px;
        line-height: 30px;
        cursor: pointer;
        background: rgba(0, 0, 0, .1);
        color: rgba(255, 255, 255, .8);
        transition: .15s;
        text-align: start;
        &.focus,
        &:hover {
            text-indent: 30px;
            background: rgba(0, 0, 0, .2);
        }
    }
}
</style>