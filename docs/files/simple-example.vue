<template>
  <VueDiagramEditor
    ref="flowx"
    :node-color="nodeColor"
    :node-pulsable="nodePulsable"
  >
    <pre slot="node" slot-scope="{node}">{{ format(node) }}</pre>
  </VueDiagramEditor>
</template>

<script>
import VueDiagramEditor from 'flowx-editor-vue';
import 'flowx-editor-vue/dist/flowx-editor-vue.css';

export default {
  name: 'simple-example',
  components: {
    VueDiagramEditor
  },
  data: () => ({
    nodes: {
      'node-1': {
        id: 'node-1',
        title: 'My node 1',
        size: {
          width: 200,
          height: 220
        },
        portsOut: {
          default: 'out port default'
        }
      },
      'node-2': {
        id: 'node-2',
        title: 'My node 2',
        size: {
          width: 200,
          height: 220
        },
        coordinates: {
          x: 280,
          y: 100
        },
        portsIn: {
          default: 'in port'
        }
      },
    },
    links: {
      'link-1': {
        id: 'link-1',
        start_id: 'node-1',
        start_port: 'default',
        end_id: 'node-2',
        end_port: 'default'
      }
    }
  }),
  mounted() {
    this.init();
  },
  methods: {
    init() {
      this.$refs.flowx.setModel({
        nodes: this.nodes,
        links: this.links
      });
    },
    format(node) {
      return JSON.stringify(node, null, 2);
    },
    nodeColor(node) {
      if (node.coordinates.x > 200) {
        return '#0f0';
      }
      if (node.coordinates.y > 200) {
        return '#f00';
      }

      return '#00f';
    },

    nodePulsable(node) {
      return node.coordinates.y > 200;
    }
  }
};
</script>

