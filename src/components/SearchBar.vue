<template>
    <div class="searchBar">
        <input
            @focusin="$emit('search-focus')"
            @focusout="$emit('search-unfocus')"
            type="text"
            name="word"
            size="30"
            placeholder="Search"
            autocomplete="off"
            inputmode="search" 
        />
    </div>
</template>
<style lang="scss">
.searchBar {
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
            color: #e4e9ed;
        }
        &:focus::placeholder {
            color: transparent;
        }
    }
    &:hover {
        width: 530px;
        background-color: rgba(15,15,15,.6);
    }
    &:focus-within {
        width: 530px;
        background-color: rgba(15,15,15,.6);
    }
}
</style>
<script lang="ts">
export default {
    name: "search-bar"
}
</script>