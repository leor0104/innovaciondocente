<template>
  <div>
    <div class="card_4"
         v-if="nota">
      <div class="card_4__thumb">
        <img :src="nota.img"
             :alt="nota.title">
      </div>
      <div class="card_4__date" v-if="nota.date">
        <span class="card_4__date__day">{{nota.date.dia}}</span>
        <span class="card_4__date__month"
              v-if="nota.date.full">{{nota.date.full | date | slice(5,9,"")}}</span>
      </div>
      <div class="card_4__body">
        <div class="card_4__category">
          <a>{{nota.type}}</a>
        </div>
        <div class="card_4__title"
             v-if="nota.title">
          <a v-if="!nota.key.id"
             :href="nota.key.name"
             target="_blank">{{nota.title | slice(0,40)}}</a>
          <nuxt-link v-if="nota.key.id"
                     :to="{name: nota.key.name, params: {id: nota.key.id}}">
            {{nota.title | slice(0,40)}}
          </nuxt-link>
        </div>
        <div class="card_4__description">
          <p class="auto-break">{{nota.description}}</p>
        </div>
        <div class="card_4__footer">
          <a v-if="!nota.key.id"
             :href="nota.key.name"
             target="_blank">Leer más</a>
          <nuxt-link v-if="nota.key.id"
                     :to="{name: nota.key.name, params: {id: nota.key.id}}">
            Leer más
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["nota"]
};
</script>

<style lang="scss" scoped>
@import "assets/card";
p {
  padding: 0.5rem;
}
</style>
