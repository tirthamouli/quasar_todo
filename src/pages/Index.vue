<template>
  <q-page padding>
    <!-- Counter -->
    <button class="counter--button" @click="count += 1">
      {{count}}
    </button>

    <!-- Input for the message -->
    <input type="text"
      v-model="message"
      @keydown.esc="clearMessage"
      @keydown.enter="alertMessage"
      v-autofocus
      :style="errorStyle"
      ref="messageInput"
    />

    <!-- Clear button -->
    <button @click="clearMessage">Clear</button>

    <!-- The message in header -->
    <h5 class="grey--border" v-if="message">{{ message }}</h5>
    <h5 class="grey--border" v-else>No message to show</h5>

    <!-- Uppercase message -->
    <p>Message uppercase: {{ messageUppercase }}</p>
    <p>Message lowercase: {{ message | toLowerCase }}</p>
  </q-page>
</template>

<script>
/* eslint-disable no-console */

export default {
  name: 'Index',
  data() {
    return {
      message: 'I love VueJS',
      count: 0,
    };
  },
  computed: {
    messageUppercase() {
      console.log('Message uppercase called');
      return this.message.toUpperCase();
    },
    errorStyle() {
      if (this.message.length > 22) {
        return {
          color: 'red',
          background: 'pink',
        };
      }
      return {};
    },
  },
  filters: {
    toLowerCase(value) {
      return value.toLowerCase();
    },
  },
  methods: {
    clearMessage() {
      this.message = '';
    },
    alertMessage() {
      // eslint-disable-next-line no-alert
      alert(this.message);
    },
  },
  directives: {
    autofocus: {
      inserted(el) {
        el.focus();
      },
    },
  },
  beforeCreate() {
    console.log('Before create');
  },
  created() {
    console.log('Created');
  },
  beforeMount() {
    console.log('Before mount');
  },
  mounted() {
    console.log('Mounted');
    console.log(this.$refs.messageInput);
  },
  beforeUpdate() {
    console.log('Before update');
  },
  updated() {
    console.log('Updated');
  },
  beforeDestroy() {
    console.log('Before destroy');
  },
  destroyed() {
    console.log('Destroyed');
  },
};
</script>

<style scoped>
.grey--border{
  border: 1px solid grey;
}

.counter--button {
  position: absolute;
  right: 10px;
}
</style>
