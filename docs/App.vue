<template>
  <div id="app">
    <div class="container">
      <section id="main">
        <Flowx ref="editor1"/>
        <Flowx ref="editor2"/>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    currentPosition: '',
    isNavSticky: false,
  }),

  mounted() {
    const model = {
      nodes: [
        {id: 'a', title: 'Component A', portsOut: {default: 'Default OUT port'}, coordinates: {x: 10, y: 10}},
        {id: 'b', title: 'Component B', portsIn: {default: 'Default IN port'}, coordinates: {x: 200, y: 10}}
      ],
      links: [
        {start_id: 'a', end_id: 'b'}
      ]
    };
    this.$refs.editor1.setModel(model);
    this.$refs.editor2.setModel(model);
  },

  methods: {

  },
};
</script>

<style lang="scss">

</style>
