<template>
    <div id="searchBar">
        <input
            @focusin="$emit('search-focus'); focus = true"
            @focusout="$emit('search-unfocus'); focus = false"
            :value="modelValue"
            @input="$emit('update:modelValue', ($event.target as HTMLInputElement).value)"
            @keyup.enter="goSearch"
            @keydown.up="$emit('move-selected', -1)"
            @keydown.down="$emit('move-selected', 1)"
            type="text"
            name="word"
            size="30"
            placeholder="Search"
            autocomplete="off"
            inputmode="search" 
        />
        <Transition>
            <span v-show="focus" style="position: fixed;" @click="goSearch">
                <i class="fa-solid fa-magnifying-glass"></i>
            </span>
        </Transition>
    </div>
</template>
<style lang="scss">
#searchBar {
    position: absolute;
    top: 200px;
    left: 50%;
    transform: translateX(-50%);
    width: 230px;
    max-width: 80%;
    height: 43px;
    border-radius: 30px;
    color: #fff;
    background-color: #ffffff40;
    box-shadow: rgba(0, 0, 0, .2) 0 0 10px;
    backdrop-filter: blur(10px) saturate(1.5);
    overflow: hidden;
    transition: color .25s, background-color .25s, box-shadow .25s, left .25s, opacity .25s, top .25s, width .25s;
    background-color: rgba(0, 0, 0, .35);
    & input {
        outline: 0;
        border: none;
        width: 80%;
        height: 100%;
        padding: 0 20px;
        color: inherit;
        background-color: transparent;
        font-size: 15px;
        font-family: var(--fonts);
        text-align: center;
        &::placeholder {
            transition: 200ms;
            color: #e4e9ed;
            opacity: 1;
        }
        &:focus::placeholder {
            opacity: 0;
        }
    }
    &:hover {
        width: 530px;
        background-color: rgba(15,15,15,.6);
    }
    &:focus-within {
        width: 530px;
        background-color: rgba(30,30,30,.9);
    }
    & span {
        transform: translateX(-10px);
        padding: 11px;
        transition: 200ms;
        cursor: pointer;
        padding-right: 20px;
        &:hover {
            background-color: rgba(105, 105, 105, 0.308);
        }
    }
}


</style>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: "search-bar",
    data() {
        return {
            focus: false
        }
    },
    props: {
        modelValue: {
            type: String,
            default: "",
            required: true
        },
        suggestWord: {
            type: String,
            default: "",
            required: true,
        }
    },
    methods: {
        goSearch() {
            if (!this.modelValue) return;
            if (this.suggestWord) {
                window.location.href = `https://www.google.com/search?q=${this.suggestWord}`;
            } else {
                window.location.href = `https://www.google.com/search?q=${this.modelValue}`;
            }
        }
    }
});
</script>