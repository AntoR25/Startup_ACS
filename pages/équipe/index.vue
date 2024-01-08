<script setup>
const query = gql`
  query Membres {
    membres {
      createdAt
      id
      publishedAt
      name
      poste
      updatedAt
      image {
        id
        handle
        fileName
        mimeType
        url
      }
      linkedin
      slug
    }
  }
`;

const { data } = await useAsyncQuery(query);
const membres = ref(data.value.membres);
</script>

<template>
  <h1 class="text-5xl font-bold mt-20">Notre Équipe</h1>
  <br>
  <section class="grid grid-cols-3 gap-10">
    <div v-for="membre in membres" :key="membre.slug"
      class="group before:hover:scale-95 before:hover:h-72 before:hover:w-80 before:hover:h-44 before:hover:rounded-b-2xl before:transition-all before:duration-500 before:content-[''] before:w-80 before:h-24 before:rounded-t-2xl before:bg-gradient-to-bl from-sky-200 via-blue-200 to-blue-700 before:absolute before:top-0 w-80 h-72 relative bg-slate-50 flex flex-col items-center justify-center gap-2 text-center rounded-2xl overflow-hidden">
      <img :src="membre.image.url" :alt="membre.name" class="w-28 h-28 mt-8 rounded-full border-4 border-slate-50 z-10 group-hover:scale-150 group-hover:-translate-x-24 group-hover:-translate-y-20 transition-all duration-500">
      <div class="z-10 group-hover:-translate-y-10 transition-all duration-500">
        <span class="text-2xl font-semibold text-black-700">{{ membre.name }}</span>
        <p class="text-black-700">{{ membre.poste }}</p>
      </div>
      <a :href="membre.linkedin" class="bg-blue-700 px-4 py-1 text-slate-50 rounded-md z-10 hover:scale-125 transition-all duration-500 hover:bg-blue-500" target="_blank">Follow</a>
    </div>
  </section>
  <br><br>
</template>


