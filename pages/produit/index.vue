<script setup>
const query = gql`
  query Produits {
    produits {
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

const { data } = await useAsyncQuery(query);
const produits = ref(data.value.produits);

</script>

<template>
  <h1 class="text-5xl font-bold mt-20">Produit</h1>
  <br>
  <p class="text-lg mb-8">Liste des sprites personnages</p>
  <section class="grid grid-cols-2 gap-10">
    <div v-for="produit in produits" :key="produit.id"
      class="p-8 border-4 my-4 rounded-lg hover:bg-gray-50">
      <a :href="produit.url" target="_blank">
        <NuxtLink :to="`/produit/${produit.slug}`">
          <h2 class="text-2xl text-indigo-800 font-semibold mb-2 hover:underline">{{ produit.titre }}</h2>
        </NuxtLink>
      </a>
      <p>{{ produit.categorie }}</p>
      
      <!-- Ajoutez la balise img pour afficher l'image -->
      <img :src="produit.image.url" :alt="produit.titre" class="w-full h-auto mt-4" />
      
      <div class="mt-4">
        <!-- Ajustez les propriétés en fonction de vos données GraphQL -->
        
      </div>
    </div>
    <br>
  </section>
  <br><br>
</template>
