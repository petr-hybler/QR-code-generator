<template lang="html">
  <div class="container">
    <form>
      <div class="form-group">
        <label for="qr-text">String for QR:</label>
        <input type="text" class="form-control" name="qr-text" value="" v-model="qr.text">
      </div>
      <div class="form-group">
          <label for="qr-size">Size:</label>
          <select class="form-control" name="qr-size"  v-model="qr.size">
            <option v-for="size in qrSize"> {{ size }} </option>
          </select>
      </div>
      <div class="form-group">
          <label for="qr-err-level">Error correction:</label>
          <select class="form-control" name="qr-err-level" v-model="qr.level">
            <option v-for="level in errLevels"> {{ level }} </option>
          </select>
      </div>
      <button @click.prevent="generateQr" class="btn btn-primary">Generate</button>
    </form>
  </div>
</template>

<script>
  import { Bus } from './../main.js';

  export default {
     data: function() {
          return {
              qr: {
                  text: 'Hello World!',
                  size: 100,
                  level: 'H'
              },
              errLevels: ['L','M','Q','H'],
              qrSize: [100,200,300,400]
          }
     },
     methods: {
       generateQr() {
          Bus.$emit('generate', this.qr);
       }
     }
  }
</script>

<style lang="css" scoped>
</style>
