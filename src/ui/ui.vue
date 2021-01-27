<template>
<div id="ui">
	<button class="button button--primary" @click='createNode'> Create a Vue3 node </button>
	<p class="type type--pos-small-normal"> {{message}} </p>
</div>
</template>

<script>
import styles from 'figma-plugin-ds/dist/figma-plugin-ds.css'
import {
  dispatch,
  handleEvent
} from "./uiMessageHandler";
import {
  onMounted,
  ref
} from 'vue';

export default {
  setup() {

    const message = ref("")

    function createNode() {
      // This shows how the UI code can send messages to the main code.
      dispatch("createNode");
    }
    onMounted(() => {

      // The following shows how messages from the main code can be handled in the UI code.
      handleEvent("nodeCreated", nodeID => {
        message.value = `Node ${nodeID} was created!`;
      });
    })

    return {
      message,
      createNode
    };
  }

};
</script>

<style scoped>
#ui{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: var(--size-medium);
}
</style>