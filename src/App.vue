<template>
  <div class="container">
    <h1>QR Code Generator</h1>
    <app-form :value="value" :size="size" :level="level"></app-form>
    <hr>
    <app-display :value="value" :size="size" :level="level" :levelNbr="levelNumeric"></app-display>
  </div>
</template>

<script>
  import { Bus } from './main.js';

  import Form from './components/Form.vue';
  import Display from './components/Display.vue';

  export default {
    data: function() {
      return {
        value: '',
        size: 0,
        level: '',
        levelNumeric: 3,
      }
    },
    components: {
      'app-form': Form,
      'app-display': Display,
    },
    created() {
      Bus.$on('generate', (data) => {
          this.value = data.text;
          this.size = data.size;
          this.level = data.level;

           if(data.level == 'L'){
             this.levelNumeric = 0;
           }else if(data.level == 'M'){
             this.levelNumeric = 1;
           }else if(data.level == 'Q'){
             this.levelNumeric = 2;
           }else if(data.level == 'H'){
             this.levelNumeric = 3;
           }else{
             this.levelNumeric = 3; // default
           }
      })
    }
  }
</script>

<style>
</style>
