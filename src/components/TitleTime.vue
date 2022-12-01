<template>
    <div class="title">
        <p>22:14</p>
    </div>
</template>
<style lang="scss">

.title {
    position: fixed;
    top: 70px;
    left: 50%;
    transform: translateX(-50%);
    padding: 10px;
    text-align: center;
    cursor: pointer;
    transition: .25s ease-in-out;
    & p {
        max-width: 300px;
        color: #fff;
        font-weight: 400;
        font-size: 42px;
        text-shadow: 0 0 20px rgba(0,0,0,.35);
        transition: .25s;
    }
    &:hover p {
        transform: scale(1.15);
    }
}

</style>
<script lang="ts">
export default {
    name:"title-time"
}
</script>