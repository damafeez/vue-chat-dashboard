<template>
  <div class="home">
    <NavBar></NavBar>
    <main>
      <h1>Chat</h1>
      <div class="chat-container">
        <div class="input-box">
          <svg class="icon">
            <use xlink:href="/icons/symbols.svg#search"></use>
          </svg>
          <input placeholder="Search" type="text">
        </div>
        <div class="details">
          <h2>Habeeb Orzil</h2>
          <p>Online</p>
        </div>
        <div class="chat-list">
          <div v-for="i in 20" :key="i" class="chat-list-item">
            <div class="img"/>
            <h3>Habeeb Orzil</h3>
            <p class="message">Early prototype of product</p>
            <p class="date">03 Feb</p>
            <span>3</span>
          </div>
        </div>
        <div class="chat-view">
        </div>
      </div>
    </main>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import NavBar from "@/components/Nav.vue";
import ChatBubble from "@/components/ChatBubble.vue";

export default Vue.extend({
  name: "home",
  components: {
    NavBar,
    ChatBubble
  }
});
</script>

<style lang="scss" scoped>
@import "@/assets/scss-tools/index.scss";
.home {
  display: flex;
  min-height: 100vh;
  main {
    background: var(--bg-color);
    box-shadow: -15px 0px 60px -27px rgba(58, 58, 58, 0.08),
      -90px 0px 100px -51px rgba(58, 58, 58, 0.09);
    flex: 1;
    padding: var(--md-space) var(--lg-space);
    .input-box {
      padding: 10px 10px 10px 0;
      margin: 0 var(--sm-space);
      display: flex;
      align-items: center;
      .icon {
        font-size: 1.2rem;
        margin-right: 10px;
      }
    }
    .details {
      flex: 1;
      h2 {
        margin: 0;
        color: var(--primary-text-color);
      }
      p {
        margin: 0;
        font-weight: 500;
      }
    }
    .details, .input-box {
      border-bottom: 1.2px solid #d1d1d8;
      align-self: end;
    color: var(--secondary-text-color);
    }
    .chat-container {
      display: grid;
      grid-template: auto auto / rem(420px) 1fr;
      grid-gap: var(--sm-space);
    }
  }
}
.chat-list {
  overflow-y: scroll;
  overflow-x: visible;
  padding: 0 var(--sm-space);
  max-height: rem(530px);
}
.chat-list-item {
  display: grid;
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 3px 3px 10px rgba(58, 58, 58, 0.05),
    -3px -3px 10px rgba(58, 58, 58, 0.05);
  padding: rem(20px);
  color: var(--secondary-text-color);
  font-weight: 500;
  font-size: 0.8rem;
  align-items: center;
  cursor: pointer;
  transition: all 0.2s ease-in;
  will-change: margin;
  margin: rem(10px) auto;
  grid-template: 1.5rem 1.5rem / auto 1fr auto;
  grid-column-gap: rem(10px);
  grid-template-areas:
    "img username date"
    "img message notification";
  &:hover {
    transform: scaleX(1.02);
    box-shadow: 10px 10px 20px rgba(58, 58, 58, 0.1);
  }
  .img {
    grid-area: img;
    width: rem(50px);
    height: rem(50px);
    border-radius: 50%;
    background-image: url("https://damafeez.github.io/MyDiary/UI/img/john.jpg");
  }
  h3 {
    color: var(--primary-text-color);
    font-size: 1rem;
    text-overflow: ellipsis;
  }
  .message {
    grid-area: message;
    text-overflow: ellipsis;
  }
  .date {
    grid-area: date;
  }
  span {
    grid-area: notification;
    justify-self: flex-end;
    @include centered-flex;
    width: 1.1rem;
    height: 1.1rem;
    color: white;
    border-radius: 50%;
    background: rgb(243, 21, 21);
    font-size: 0.7rem;
  }
}
</style>

