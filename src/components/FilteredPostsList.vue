<template>
  <div class="flex">
    <div class="first-column" :class="{ column: !isDisplayed }">
      <p class="column-header">Column with filter</p>
      <div class="column-header">
        <input
          :value="value"
          @input="$emit('input', $event.target.value)"
          @keyup.enter="$emit('click')"
        />
        <button @click="$emit('click')">Do it!</button>
      </div>
      <ul>
        <li v-for="(post, index) in results" :key="post.id">
          <span class="post-number">{{ index + 1 }}.</span> {{ post.title }}
        </li>
      </ul>
    </div>
    <div class="column">
      <div class="column-header">
        <input v-model="isDisplayed" type="checkbox" />
        <p v-if="!isDisplayed">Mark to hide this column</p>
        <p v-else>Mark to show online filtering version</p>
      </div>
      <div :class="{ 'hide-column': isDisplayed }">
        <p class="column-header">Value to make online filtering: {{ value }}</p>
        <ul>
          <li v-for="(post, index) in onlineResults" :key="post.id">
            <span class="post-number">{{ index + 1 }}.</span> {{ post.title }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
  data: () => ({
    isDisplayed: false,
  }),
  props: {
    value: {
      type: String,
      default: "",
    },
    results: {
      type: Array,
    },
    onlineResults: {
      type: Array,
    },
  },
};
</script>
<style>
.flex {
  display: flex;
}
.column {
  flex-basis: 50%;
}
.column-header {
  display: flex;
  justify-content: center;
  font-weight: bold;
}
p {
  margin: 0;
}
li {
  padding-top: 5px;
  padding-bottom: 5px;
}
li:nth-child(even) {
  background: rgb(210, 240, 255);
}
ul {
  list-style-type: none;
}
.post-number {
  color: rgb(50, 50, 50);
}
.hide-column {
  display: none;
}
</style>