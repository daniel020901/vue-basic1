<template>
     <transition name="custom" enter-active-class="animated fadeInDown" leave-active-class="animated slideOutRight">
            <div v-if="sliderStatus">
                <div class="align-items-center" :class="sliderState">
                    <label for="" class="font-weight-bold-mr-2">Max</label>
                    <input type="text" class="form-control mx-2"
                        style="width: 60px; text-align: Center;" v-model="maxAmount" @change="$emit('update:maximum', maxAmount)">
                    <input type="range" clas="custom-range" min="0" max="200" v-model="maxAmount" @input="$emit('update:maximum', maxAmount)">
                </div>
            </div>
        </transition>
</template>

<script>
export default {
    name:"slider-status",
    data: function() {
        return {
            maxAmount: 50
        }
    },
    props:["sliderStatus", "maximum"],
    computed: {
        sliderState: function () {
      return this.style.sliderStatus ? "d-flex" : "d-none";
    },
    }
}
</script>

<style>
.navbar{
    background-color: transparent;
}
.fade-enter, .fade-leave-to {
    opacity: 0;
}

.fade-enter-active, .fade-leave-active {
    transition: all 3s ease-in-out;
}


</style>