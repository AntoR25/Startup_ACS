<script setup>
import { useRoute } from 'vue-router';

const query = gql`
  query Membre {
    membre {
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

const route = useRoute();
const { data } = await useAsyncQuery(query, {
  slug: route.params.slug,
});

const membre = ref(data.value.membre);
</script>

<template>
  <br><br>
  <Head v-if="membre">
    <Title>{{ membre.name }} - Détails du Membre de l'Équipe</Title>
    <Meta
      name="description"
      :content="`Découvrez des détails sur ${membre.name}: ${membre.poste}`"
    />
    <Meta
      property="og:title"
      :content="`${membre.name} - Détails du Membre de l'Équipe`"
    />
    <Meta
      property="og:description"
      :content="`Découvrez des détails sur ${membre.name}: ${membre.poste}`"
    />
    <!-- Ajoutez des propriétés supplémentaires en fonction de la structure de votre modèle -->
  </Head>

  <div v-if="membre" class="max-w-full flex flex-col md:flex-row mx-auto p-8 bg-white rounded-lg shadow-md">
    <img class="w-full md:w-1/2 h-auto rounded mb-4 md:mb-0 md:mr-4" :src="membre.image.url" :alt="membre.name" />

    <div class="md:w-1/2 flex flex-col justify-center">
      <div class="text-center">
        <h2 class="text-3xl mb-4">{{ membre.name }}</h2>
        <p class="text-red-950">{{ membre.poste }}</p>
        <!-- Ajoutez d'autres informations sur le membre de l'équipe en fonction de votre modèle -->
        <div class="my-8">
          <a class="text-sm font-semibold inline-block py-2 px-4 rounded-lg text-gray-100 bg-blue-500 uppercase last:mr-0 mr-4">
            <Icon name="pajamas:label" size="1.5rem" class="text-gray-100 mr-2" /> Catégorie: {{ membre.categorie }}
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
