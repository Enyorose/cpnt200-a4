<template>
  <div class="container flex flex-col border m-1">
    <figure class= "text-center">
      <h3>{{ info.title }}</h3>
      <figcaption>{{ info.description }}</figcaption>
      <p>{{ info.difficulty }}</p>
    </figure>
  </div>
</template>
<script>
export default {
  props: ['info']
}
</script>
