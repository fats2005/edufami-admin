<template>
  <v-card>
    <v-card-title v-for="(item,key) in unit" :key="key">
      <div>
        <span class="grey--text">{{key}}</span>
        <br>
        <span>{{item}}</span>
      </div>
    </v-card-title>
  </v-card>
</template>

<script>
export default {
  props: {
    unit: Object
  }
};
</script>

