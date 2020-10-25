<template>
  <dialog :open="open" class="card" v-on:keyup.esc="dismissCard">
    <button
      v-if="dismissable"
      class="close-btn"
      aria-label="Close card"
      @click="dismissCard"
    >
      X
    </button>
    <slot />
    <button class="btn">
      Click me!
    </button>
  </dialog>
</template>

<script>
export default {
  name: 'Card',
  props: ['open', 'dismissable'],
  methods: {
    dismissCard: function() {
      this.open = false;
    },
  },
};
</script>

<style lang="scss">
.card {
  max-width: 70%;
  width:400px;
  margin-bottom: 40px;
  padding: 0.5em 1em;
  background-color: rgb(255, 255, 255);
  border-radius: 6px;
  .close-btn {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    background: transparent;
    border: 0 transparent;
    font-size: 1.5em;
    position: absolute;
    right: 5px;
    top: 5px;
  }
  .btn {
    border: 1px solid #ff7a59;
    background-color: #ff7a59;
    border-radius: 3px;
    color: #ffffff;
    font-size: 1rem;
    padding: 11px 24px;
    text-align: center;
    user-select: none;
    transition: all 0.15s ease-out;
    display: inline-block;
    max-width: 100%;
    overflow: hidden;
    text-overflow: ellipsis;
    vertical-align: middle;
    white-space: nowrap;
    &:hover {
      background-color: #ff8f73;
      border-color: #ff8f73;
      color: #ffffff;
      cursor: pointer;
    }
  }
}
</style>
