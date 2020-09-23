<template>
  <div class="message-bar" :message="message">
    <div class="text-message" v-if="message.messageType === 'text'">
      {{ message.text }}
    </div>
    <!--<div class="img-message" v-else-if="message.messageType === 'img'">
      <img :src="message.imgUrl" alt="" />
    </div>-->
    <img
      class="img-message"
      v-else-if="message.messageType === 'img'"
      :src="message.imgUrl"
      alt=""
    />
    <div class="link-message" v-else-if="message.messageType === 'link'">
      <a href="#">
        <div class="order-info" v-if="message.linkType === 'order'">
          <span class="orderId">订单号:{{ message.order.orderId }}</span>
          <span class="orderDate">{{ message.order.orderDate }}</span>
        </div>
        <div class="item-info">
          <div class="item-img">
            <img :src="message.item.imgUrl" alt="" />
          </div>
          <div class="item-detail">
            <div class="item-name">
              {{ message.item.name }}
            </div>
            <div class="item-addition">
              <div class="item-price">
                {{ message.item.price }}
              </div>
              <div class="order-status" v-if="message.linkType === 'order'">
                {{ message.order.status }}
              </div>
            </div>
          </div>
        </div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "MessageBar",
  props: {
    message: {
      type: Object,
      required: true
    }
  }
};
</script>

<style scoped>
.message-bar {
}
.text-message {
  width: fit-content;
  width: -moz-fit-content;
  border: #d1d8e5 1px solid;
  padding: 5px;
  border-radius: 5px;
  margin-left: 10px;
  margin-top: 5px;
}
.img-message {
  display: block;
  margin-left: 10px;
  margin-top: 5px;
}
.link-message {
  width: 450px;
  padding: 10px;
  margin-top: 5px;
  margin-left: 10px;
  border: #d1d8e5 1px solid;
}
.link-message a {
  width: 400px;
  display: inline-block;
}

.order-info {
  height: 30px;
}
.order-info span{
  display: block;
}
.orderId {
  float: left;
}
.orderDate {
  float: right;
}
.item-info {
  height: 100px;
}
.item-img {
  display: block;
  float: left;
  width: 90px;
  height: 90px;
  margin-left: 10px;
  margin-top: 5px;
}
.item-detail {
  float: left;
  width: 280px;
  margin-left: 5px;
  margin-top: 5px;
  height: 90px;
}
.item-name {
  height: 45px;
  word-wrap: break-word;
  text-align: left;
}
.item-addition {
  height: 45px;
}
.item-price {
  height: 45px;
  width: 100px;
  float: left;
  text-align: left;
  line-height: 45px;
}
.order-status {
  height: 45px;
  width: 100px;
  float: right;
  line-height: 45px;
  text-align: right;
}
</style>
