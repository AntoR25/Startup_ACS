<script setup>
const { data: posts } = await useAsyncData('posts', () =>
  queryContent('/blog').find()
)
</script>

<template>
  <h1 class="text-3xl my-8">Articles de Blog</h1>

  J'aime écrire sur tout ce sur quoi je travaille actuellement ou quelque chose de nouveau qui m'intéresse. Si vous souhaitez que
  j'écrive sur quelque chose ou que je sois un blogueur invité sur votre blog, n'hésitez pas à me contacter sur Twitter. Si vous souhaitez
  vous abonner à un flux RSS, vous pouvez le trouver ici.

  <section class="grid md:grid-cols-3 mt-8 gap-10">
    <Post :posts="posts" />
  </section>
  <br><br>
</template>
