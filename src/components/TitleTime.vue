<template>
    <div class="title">
        <p>{{hours}}:{{minutes}}</p>
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
import { defineComponent } from 'vue';
export default defineComponent({
    name:"title-time",
    data() {
        return {
            hours: "",
            minutes: ""
        }
    },
    methods: {
        getTimeNow() {
            const zerofilled = (num:number) => ('00' + num).slice(-2);
            const dateObj =  new Date();
            this.hours = zerofilled(dateObj.getHours());
            this.minutes = zerofilled(dateObj.getMinutes());
        }
    },
    created() {
        this.getTimeNow();
        setInterval(this.getTimeNow, 1000);
    }
});
</script>