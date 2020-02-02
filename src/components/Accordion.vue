<template>
    <div class="accordion-wrapper">
      <div class="accordion-item" v-for="item in accordionContent" :key="item.id">
        <div class="accordion-title" @click="item.active = !item.active"
                                     :class="{ 'is-open' : item.active }">{{ item.title }}</div>
        <transition name="fade">
          <div class="accordion-content" v-show="item.active" v-html="item.description"></div>
        </transition>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Accordion',
  props: {
    accordionContent: Array
  },
}
</script>