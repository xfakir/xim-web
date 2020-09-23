<template>
  <div class="chat" :mode="mode">
    <div class="personal" v-if="mode === 'contact'"></div>
    <div class="chat-list"></div>
    <div class="main">
      <div class="chat-header"></div>
      <div class="chat-wrapper">
        <div class="chat-main">
          <div class="chat-content"></div>
          <div class="chat-input"></div>
        </div>
        <div class="chat-addition"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ChatCard",
  props: {
    mode: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.chat-header{}

</style>
