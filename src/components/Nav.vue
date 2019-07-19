<template>
  <nav>
    <img src="https://damafeez.github.io/MyDiary/UI/img/john.jpg" alt="profile-image">
    <p>
      <span>Jimmi Hendrix</span>
      <svg class="icon">
        <use xlink:href="/icons/symbols.svg#chevron-down"></use>
      </svg>
    </p>
    <ul>
      <li
        v-for="(link, i) in links"
        :key="i"
        :class="{active: activeIndex === i}"
        @click="() => activeIndex = i"
      >
        <svg class="icon">
          <use :xlink:href="`/icons/symbols.svg#${link.icon}`"></use>
        </svg>
        <span>{{link.title}}</span>
      </li>
    </ul>
  </nav>
</template>
<script lang="ts">
import Vue from "vue";
import links from "@/data/fixtures/navLinks";
export default Vue.extend({
  name: "nav",
  data() {
    return {
      links,
      activeIndex: 0
    };
  }
});
</script>


<style lang="scss" >
@import "@/assets/scss-tools/index.scss";

nav {
  background: var(--primary-color);
  display: flex;
  flex-direction: column;
  align-items: center;
  width: rem(250px);
  padding: var(--md-space) var(--sm-space);

  p {
    font-weight: 700;
    display: flex;
    align-items: center;
    .icon {
      font-size: 1.2rem;
      margin-left: rem(10px);
    }
  }

  ul {
    align-self: stretch;
    margin: var(--sm-space) calc(var(--sm-space) * -1) 0;
    text-transform: uppercase;
    color: var(--secondary-text-color);
    font-weight: 500;
    li {
      padding: 5px var(--sm-space);
      margin: var(--sm-space) 0;
      cursor: pointer;
      display: flex;
      align-items: center;
      border-left: 3.5px solid transparent;
      will-change: border-left-color;
      transition: all .2s ease-in;
      &.active {
        color: var(--accent-text-color);
        border-left-color: var(--accent-text-color);
      }
      .icon {
        font-size: 1.1rem;
        margin-right: var(--sm-space);
        will-change: color;
      }
    }
  }

  img {
    width: rem(100px);
    height: rem(100px);
    border: 3px solid var(--bg-color);
    border-radius: 50%;
    box-shadow: 5px 12px 20px rgba(#000, 0.15);
  }
}
</style>
