<template>
  <div id="stats">
    <div id="stats__day">Day {{ player.day }}</div>
    <details>
      <summary id="stats__employee-count">
        {{ player.employees.count }} Employees
        <span title="NPS score"> {{ employeeNPSEmoji }} </span>
      </summary>
      <div id="stats__employee-nps">
        Employee NPS: {{ player.employees.nps }}
      </div>
    </details>
    <details>
      <summary id="stats__customer-count">
        {{ player.customers.count }} Customers
      </summary>
      <div id="stats__customer-nps">
        Customer NPS: {{ player.customers.nps }}
        <span title="NPS score"> {{ customerNPSEmoji }} </span>
      </div>
    </details>
    <details>
      <summary id="stats__flywheel">Flywheel</summary>
      <div id="stats__flywheel-attract">
        Attract: {{ player.flywheel.attract }}
      </div>
      <div id="stats__flywheel-engage">
        Engage: {{ player.flywheel.engage }}
      </div>
      <div id="stats__flywheel-delight">
        Delight: {{ player.flywheel.delight }}
      </div>
    </details>
    <div id="stats__money" :class="{ 'text-red': isMoneyNegative }">
      $ {{ player.money }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'GameStats',
  props: ['player'],
  computed: {
    isMoneyNegative: function() {
      if (this.player.money < 1) {
        return true;
      } else {
        return false;
      }
    },
    employeeNPSEmoji: function() {
      return this.NPSEmoji(this.employeeNPS);
    },
    customerNPSEmoji: function() {
      return this.NPSEmoji(this.customerNPS);
    },
  },
  methods: {
    NPSEmoji(nps) {
      if (nps > 8) {
        return '😍';
      }
      if (8 > nps > 7) {
        return '😊';
      }
      if (7 > nps > 6) {
        return '😀';
      }
      if (6 > nps > 5) {
        return '😐';
      }
      if (5 > nps > 4) {
        return '😕';
      }
      if (4 > nps > 2) {
        return '😔';
      }
      if (nps == 1) {
        return '😠';
      }
    },
  },
};
</script>

<style lang="scss">
#stats {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  width: 100%;
  padding: 5px 0;
  min-height: 50px;
}
#stats__money {
  color: green;
}
#stats__money.text-red {
  color: red;
}
</style>
