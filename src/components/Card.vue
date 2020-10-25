<template>
  <dialog :open="open" class="cms-vue-boilerplate-card">
    <p>
      {{ reasonsText }}
    </p>
    <button class="btn">
      Click me!
    </button>
  </dialog>
</template>

<script>
const pluralize = (n, noun, suffix) =>
  `${n !== 1 ? 'are' : 'is'} ${n} ${noun + (n !== 1 ? suffix : '')}`;

export default {
  name: 'Card',
  props: ['open'],
  
  computed: {
    reasonsText() {
      return `There are ${
        this.reasonsCount > 0
          ? pluralize(this.reasonsCount, 'reason', 's')
          : 'so many reasons'
      } to use HubSpot CMS + Vue!`;
    },
  },
  methods: {
    increaseClickCount() {
      this.reasonsCount += 1;
    },
  },
};
</script>

<style lang="scss">
.cms-vue-boilerplate-card {
  max-width: 500px;
  margin-bottom: 40px;
  padding: 0.5em 1em;
  background-color: rgb(255, 255, 255);
  border-radius: 6px;
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
