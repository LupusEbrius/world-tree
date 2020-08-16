<template>
    <div v-if="this.isEdit==false">
        <h3>{{ title }}</h3>
        <p>{{ value }}</p>
    </div>
    <div v-else>
        <h3>{{ title }}</h3>
        <div v-if="options=='textarea'">
          <textarea rows="10" cols="50" v-model="value"/>
        </div>
        <div v-else>
          <input type="text" name="desc" :id="title.split('_')[0]" v-model="value">
        </div>
    </div>
</template>
<script>
export default {
  name: 'Display',
  props: {
    title: String,
    value: String,
    options: String,
    isEdit: Boolean
  }
}
</script>

<style scoped>
  textarea {
    resize: none;
    overflow: auto;
  }
</style>
