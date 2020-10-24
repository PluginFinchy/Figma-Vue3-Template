<template>
<div>
	<button class="button button--primary" @click='createNode'> Create a node </button>
	<p class="type type--pos-small-normal"> {{message}} </p>
</div>
</template>

<script>
import { dispatch, handleEvent } from "./uiMessageHandler";

// Add these lines to import the interactive figma-ui components as needed.
import "./figma-ui/js/selectMenu";
import "./figma-ui/js/iconInput";
import "./figma-ui/js/disclosure";

export default {
  data() {
    return {
      message: ""
    };
  },
  mounted() {
    // Add these lines to initialize the interactive figma-ui components as needed.
    window.selectMenu.init();
    window.iconInput.init();
    window.disclosure.init();

    // The following shows how messages from the main code can be handled in the UI code.
    handleEvent("nodeCreated", nodeID => {
      this.message = `Node ${nodeID} was created!`;
    });
  },
  methods: {
    createNode() {
      // This shows how the UI code can send messages to the main code.
      dispatch("createNode");
    }
  }
};
</script>

<style lang='scss'>
@import "./figma-ui/figma-plugin-ds";
</style>