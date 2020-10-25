<template>
  <div class="game-container">
    <GameStats :player="player" :serverInitial="moduleData.serverInitial" />
    <Card :open="cardDisplayed" :dismissable="true"/>
  </div>
</template>

<script>
import Card from '@/components/Card.vue';
import GameStats from '@/components/GameStats.vue';


export default {
  name: 'App',
  props: ['moduleData'],
  data: function() {
    return {
      player: {
        day: 1,
        money: 0,
        employees: {
          count: 0, //number of employees
          nps: 1, //current employee NPS
        },
        customers: {
          count: 0, // number of customers
          nps: 1, // current customer NPS
        },
        flywheel: {
          attract: 0,
          engage: 0,
          delight: 0,
        },
      },
      cardDisplayed: true,
      cardDismissable: true
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
    GameStats,
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
  font-size: calc(10px + .5vw);
  color: white;
  padding: 1rem 0 1rem 0;
}
</style>
