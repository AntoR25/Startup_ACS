<script setup>
import { useRoute } from 'vue-router';

const query = gql`
  query Produit($slug: String!) {
    produit(where: { slug: $slug }) {
      createdAt
      id
      publishedAt
      texte
      titre
      categorie
      updatedAt
      slug
      image {
        id
        handle
        fileName
        mimeType
        url
      }
    }
  }
`;

const route = useRoute();
const { data } = await useAsyncQuery(query, {
  slug: route.params.slug,
});

const produit = ref(data.value.produit);
</script>


<template>
  <br><br>
  <Head v-if="produit">
    <Title>{{ produit.titre }} - Détails du Produit</Title>
    <Meta
      name="description"
      :content="`Découvrez des détails sur ${produit.titre}: ${produit.texte}`"
    />
    <Meta
      property="og:title"
      :content="`${produit.titre} - Détails du Produit`"
    />
    <Meta
      property="og:description"
      :content="`Découvrez des détails sur ${produit.titre}: ${produit.texte}`"
    />
    <!-- Update properties accordingly based on your produit structure -->
  </Head>

  <div v-if="produit" class="max-w-full flex flex-col md:flex-row mx-auto p-8 bg-white rounded-lg shadow-md">
    <img class="w-full md:w-1/2 h-auto rounded mb-4 md:mb-0 md:mr-4" :src="produit.image.url" :alt="produit.titre" />

    <div class="md:w-1/2 flex flex-col justify-center">
      <div class="text-center">
        <h2 class="text-3xl mb-4">{{ produit.titre }}</h2>
        <p class="text-red-950">{{ produit.texte }}</p>
        <div class="my-8">
    <a class="text-sm font-semibold inline-block py-2 px-4 rounded-lg text-gray-100 bg-blue-500 uppercase last:mr-0 mr-4">
      <Icon name="pajamas:label" size="1.5rem" class="text-gray-100 mr-2" /> {{ produit.categorie }}
    </a>
  </div>
      </div>
    </div>
  </div>

  <div v-else class="flex items-center justify-center h-screen">
    <span class="text-lg">Chargement en cours...</span>
  </div>
  <br><br><br>
</template>