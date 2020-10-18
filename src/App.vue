<template>
  <div class="game-container">
    
    
    <Card :initialClickCount="moduleData.initial_count" />
  </div>
</template>

<script>
import Card from '@/components/Card.vue';
import SpinningLogo from '@/components/SpinningLogo.vue';
import sprocketLogo from '@/assets/sprocket.svg';
import vueLogo from '@/assets/vue.svg';

export default {
  name: 'App',
  props: ['moduleData'],
  data: function() {
    return {
      sprocketLogo,
      vueLogo,
      money:0,
      employee_count:0,
      employee_nps:0,
      customer_nps:0,
      customer_count:0,
      flywheel:{
        attract: 0,
        engage:0,
        delight:0,
      }

    };
  },
  created: function() {
    // eslint-disable-next-line no-console
    console.log(
      'all of your data typically accessed via the "module" keyword in HubL is available as JSON here!',
      this.moduleData,
    );
  },
  components: {
    Card,
    SpinningLogo,
  },
};
</script>

<style lang="scss">
.game-container {
  text-align: center;
  background-color: #282c34;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
  padding: 1rem 0 1rem 0;
}


</style>
