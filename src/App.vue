<template>
  <div id="app">
    <Header>
      <h3>VueGram</h3>
    </Header>

    <Card></Card>
    <Card></Card>
    <Card></Card>
  </div>
</template>

<script>
import Header from './components/header.vue'
import Card from './components/card.vue'

export default {
  name: 'app',
  components: {
    Header,
    Card
  }
}
</script>
