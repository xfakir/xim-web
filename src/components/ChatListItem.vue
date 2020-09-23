<template>
  <div
    class="item"
    :avatar="avatar"
    :itemName="itemName"
    :lastMessage="lastMessage"
    :lastMessageTime="lastMessageTime"
    :height="height"
    :style="{ height: height + 'px' }"
  >
    <div class="avatar-box">
      <div class="avatar">
        <img :src="avatar" alt="" height="30" width="30" />
      </div>
    </div>
    <div class="content">
      <span class="chat-name">
        {{ itemName }}
      </span>
      <span class="last-msg">
        {{ lastMessage }}
      </span>
    </div>
    <div class="time">
      <span class="time-box">{{ lastMessageTime }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "ChatListItem",
  props: {
    avatar: {
      type: String
    },
    itemName: {
      type: String
    },
    lastMessage: {
      type: String
    },
    lastMessageTime: {
      type: String
    },
    height: {
      type: Number
    }
  }
};
</script>

<style scoped>
.avatar-box {
  width: 40px;
  float: left;
}
.content {
  width: 120px;
  float: left;
}
.time {
  width: 40px;
  float: left;
}

.avatar {
  width: 30px;
  height: 30px;
  margin-left: 5px;
  margin-top: 10px;
}
.content {
  font-size: 14px;
}
.content span {
  display: block;
  text-align: left;
}
.chat-name {
  margin-left: 5px;
  margin-top: 8px;
}
.last-msg {
  margin-left: 5px;
}
.time {
  font-size: 14px;
}
.time span {
  display: block;
}
.time-box {
  margin-top: 8px;
}
</style>
