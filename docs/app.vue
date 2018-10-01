<template>

<div>
  <div class="row">
    <h1>Emoji Mart Vue 🏬</h1>
  </div>

  <div class="row">
    <template v-for="set in ['native', 'apple', 'google', 'twitter', 'emojione', 'messenger', 'facebook', 'test']">
      <button :key="set" @click="activeSet = set" :disabled="activeSet == set">{{ set }}</button>
    </template>
  </div>

  <div class="row">
    <picker
      :set="activeSet"
      :data="customData"
      :native="native"
      :emoji="emoji"
      :title="title"
      :recent="[]"
      :emojiSize="28"
      :showPreview="false"
      :showCategories="true"
      :showSearch="false"
    />
  </div>

  <div class="row-small">
    <iframe
      src="https://ghbtns.com/github-btn.html?user=jm-david&repo=emoji-mart-vue&type=star&count=true"
      frameBorder="0"
      scrolling="0"
      width="90px"
      height="20px"
    ></iframe>
  </div>
</div>

</template>

<script>

import { Picker, Emoji } from '../src'
import customData from './customData.json'

const CUSTOM_EMOJIS = [
  {
    name: 'Party Parrot',
    short_names: ['parrot'],
    keywords: ['party'],
    imageUrl: './images/parrot.gif',
    custom: true
  },
  {
    name: 'Octocat',
    short_names: ['octocat'],
    keywords: ['github'],
    imageUrl: 'https://assets-cdn.github.com/images/icons/emoji/octocat.png?v7',
    custom: true
  },
  {
    name: 'Squirrel',
    short_names: ['shipit', 'squirrel'],
    keywords: ['github'],
    imageUrl: 'https://assets-cdn.github.com/images/icons/emoji/shipit.png?v7',
    custom: true
  },
]

export default {
  data() {
    return {
      activeSet: 'test',
      emoji: 'parrot',
      title: 'Pick your emoji…',
      custom: CUSTOM_EMOJIS,
      customData
    }
  },
  computed: {
    native () {
      return this.activeSet == 'native'
    }
  },
  components: {
    Picker,
    Emoji
  }
}

</script>

<style scoped>

button + button { margin-left: .5em }
button {
  padding: .4em .6em;
  border-radius: 5px;
  border: 1px solid rgba(0, 0, 0, .1);
  background: #fff;
  outline: 0;
  cursor: pointer;
}

button[disabled] {
  border-color: #ae65c5;
  cursor: default;
}

h1 {
  font-family: Courier;
}

.row + .row {
  margin-top: 2em;
}

.row-small {
  margin-top: 1em;
}

.emoji-mart {
  margin: 0 auto;
  text-align: left;
}

.emoji-mart-title-label {
  font-size: 21px;
}

</style>
