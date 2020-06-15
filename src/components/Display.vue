<template lang="html">
  <div class="row center-block text-center">
        <div class="col-xs-6">
          <h2>Regular QR</h2>
          <qrcode-vue :value="value" :size="size" :level="level"></qrcode-vue>
        </div>
        <div class="col-xs-6">
          <H2>QR with logo</h2>
          <vue-qr :text="value"
                  :size="size*1.1"
                  :correctLevel="levelNbr"
                  :dot-scale="1"
                  :logoMargin="3"
                  :margin="0"
                  logoSrc="https://cdn.iconscout.com/icon/free/png-256/vue-282497.png"></vue-qr>
        </div>
  </div>
</template>

<script>
  import QrcodeVue from 'qrcode.vue';
  import VueQr from 'vue-qr';

  export default {
    props: ['value','size','level','levelNbr'],
    data: function(){
       return {
       }
    },
    components: {
      QrcodeVue,
      VueQr,
    }
  }
</script>

<style lang="css" scoped>
</style>
