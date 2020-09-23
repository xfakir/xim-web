<template>
  <div class="service-wrapper">
    <div class="left-bar">
      <div class="personal-info">
        <div class="info-box">
          <div class="avatar">
            <img
              src="https://kodo.xfakir.cn/avatar.jpg"
              alt=""
              height="50"
              width="50"
            />
          </div>
          <div class="info">
            <p class="info-name">xxxx</p>
          </div>
        </div>
        <div class="search-box">
          <label>
            <input type="text" placeholder="搜索" v-model="search" />
          </label>
        </div>
      </div>
      <div class="chat-list">
        <div
          v-for="(service, index) in serviceList"
          :key="index"
          :class="{ serviceHover: hoverChatIndex === index }"
          @mouseenter="serviceEnter(index)"
          @click="serviceSelect(service)"
        >
          <chat-list-item
            class="service"
            :avatar="service.avatar"
            :item-name="service.itemName"
            :last-message="service.lastMessage"
            :last-message-time="service.lastMessageTime"
            :height="50"
          ></chat-list-item>
        </div>
      </div>
    </div>
    <div class="main">
      <div class="chat-header">
        <span class="chat-name">{{ currentChat.chatName }}</span>
      </div>
      <div class="chat-wrapper">
        <div class="chat-main">
          <div class="chat-content">
            <message-bar
              v-for="(message, index) in messages"
              :key="index"
              :message="message"
            ></message-bar>
          </div>
          <div class="chat-input">
            <label>
              <input type="text" placeholder="搜索" v-model="search" />
            </label>
          </div>
        </div>
        <div class="chat-addition"></div>
      </div>
    </div>
  </div>
</template>

<script>
import ChatListItem from "@/components/ChatListItem";
import MessageBar from "@/components/MessageBar";
export default {
  name: "ServiceMode",
  components: { MessageBar, ChatListItem },
  data() {
    return {
      search: "",
      hoverChatIndex: -1,
      chatItem: {
        avatar: "https://kodo.xfakir.cn/avatar_tb.jpg",
        itemName: "chat1",
        lastMessage: "last",
        lastMessageTime: "5:22"
      },
      serviceList: [
        {
          avatar: "https://kodo.xfakir.cn/avatar_tb.jpg",
          itemName: "chat1",
          lastMessage: "last",
          lastMessageTime: "5:22"
        },
        {
          avatar: "https://kodo.xfakir.cn/avatar_tb.jpg",
          itemName: "chat2",
          lastMessage: "last",
          lastMessageTime: "5:22"
        },
        {
          avatar: "https://kodo.xfakir.cn/avatar_tb.jpg",
          itemName: "chat3",
          lastMessage: "last",
          lastMessageTime: "5:22"
        }
      ],
      currentChat: {
        chatName: ""
      },
      messages: [
        {
          messageType: "text",
          text: "text message"
        },
        {
          messageType: "img",
          imgUrl: "https://kodo.xfakir.cn/avatar.jpg"
        },
        {
          messageType: "link",
          linkType: "order",
          order: {
            orderId: "order id",
            orderDate: "2020-02-20",
            status: "order status"
          },
          item: {
            name: "item1ssssssssssssssssssssssssssssssssssssssssssssssssssss",
            imgUrl: "https://kodo.xfakir.cn/avatar_tb.jpg",
            price: 1023
          }
        },
        {
          messageType: "link",
          item: {
            name: "item1",
            imgUrl: "https://kodo.xfakir.cn/avatar_tb.jpg",
            price: 1023
          }
        }
      ]
    };
  },
  methods: {
    serviceEnter(index) {
      this.hoverChatIndex = index;
    },
    serviceSelect(service) {
      this.currentChat.chatName = service.itemName;
    }
  }
};
</script>

<style scoped>
.service-wrapper {
  width: 1070px;
  height: 650px;
  background-color: #fff;
  border: #d1d8e5 1px solid;
}
.left-bar {
  width: 200px;
  height: 650px;
  float: left;
  border-right: #d1d8e5 1px solid;
}
.personal-info {
  height: 100px;
  border-bottom: #d1d8e5 1px solid;
}
.info-box {
  height: 70px;
}
.avatar {
  height: 50px;
  width: 50px;
  float: left;
  margin-top: 10px;
  margin-left: 20px;
}
.info {
  height: 50px;
  width: 100px;
  float: left;
  margin-top: 10px;
  margin-left: 10px;
}
.info-name {
  margin: 0;
}
.search-box {
  padding-top: 3px;
  padding-left: 15px;
}
.search-box input {
  border-radius: 5px;
}
.chat-list {
  width: inherit;
  height: 550px;
}

.service {
  height: 50px;
  width: inherit;
}
.serviceHover {
  background-color: #d1d8e5;
}
.main {
  width: 869px;
  height: 650px;
  float: left;
}
.chat-header {
  height: 80px;
  width: 869px;
  border-bottom: #d1d8e5 1px solid;
}

.chat-name {
  display: block;
  float: left;
  margin-top: 30px;
  margin-left: 20px;
  font-size: 20px;
}

.chat-wrapper {
  height: 570px;
  width: 890px;
}
.chat-main {
  height: inherit;
  width: 650px;
  float: left;
  border-right: #d1d8e5 1px solid;
}
.chat-content {
  height: 420px;
  width: inherit;
  border-bottom: #d1d8e5 1px solid;
  /*background-color: #e2e2e2;*/
}
.chat-input {
  height: inherit;
  width: inherit;
}
</style>
