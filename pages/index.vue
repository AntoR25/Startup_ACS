<script setup>
const { data: posts } = await useAsyncData('latest-posts', () =>
  queryContent('/blog')
    .sort({ data: 1 })
    .limit(3)
    .find()
)
</script>

<template>
  <section>
    <h1 class="text-5xl font-bold mt-20">
      <span style="color: #29ABE2;">A</span>nime
      <span style="color: #29ABE2;">C</span>haracter
      <span style="color: #29ABE2;">S</span>prite
    </h1>
    <p class="text-base text-gray-1300 border-l-4 border-black pl-4 italic my-4">
      Explorons ensemble l'univers de l'anime et de ses personnages
    </p>
  </section>
  <section class="flex flex-col md:flex-row">
    <div class="md:w-3/4">
      <h2 class="text-3xl font-bold mb-4 mt-3">Notre Histoire</h2>
      <hr class="mt-3 border-t-4 border-blue-400 w-40">
      <p class="text-lg py-1">
        Nous sommes une équipe passionnée chez Anime Character Sprite, spécialisée dans la création de sprites uniques tirés de vos animes préférés. Notre mission est de fournir des ressources graphiques de haute qualité aux créateurs, aux développeurs et aux amateurs d'anime, afin d'enrichir leurs projets visuels avec des personnages inoubliables.
      </p>
      <hr class="mt-3 border-t-4 border-blue-400 w-40">
      <p class="text-lg py-1">
        Forts d'une expérience cumulée de plus de 20 ans, nous sommes des autodidactes convaincus que la passion et le travail acharné sont les clés du succès. Nous mettons nos connaissances et notre dévouement au service de la communauté des créateurs pour les aider à atteindre leurs objectifs.
      </p>
      <hr class="mt-3 border-t-4 border-blue-400 w-40">
      <p class="text-lg py-1">
        Chez Anime Character Sprite, nous croyons en la diversité des personnages et nous nous engageons à offrir une bibliothèque variée et constamment mise à jour. Nous sommes fiers de contribuer à la réalisation de projets uniques et inspirants.
      </p>
    </div>
    <img src="https://remacle-antoine.be/icones/samourail%202.jpg" class="w-1/2 md:max-w-sm p-8 mx-auto" />
  </section>

  <section>
    <h2 class="text-3xl font-bold mt-8">Derniers articles publiés</h2>
    <div class="grid md:grid-cols-3 pt-8 gap-10 pb-8">
      <Post :posts="posts" />
    </div>
  </section>

  <!-- Balises META pour améliorer le SEO -->
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Anime Character Sprite - Explorez l'univers de l'anime avec des sprites uniques. Découvrez notre histoire, nos créations, et les derniers articles publiés.">
    <meta name="keywords" content="anime, sprite, personnages, créations, articles">
    <meta name="author" content="Anime Character Sprite">
    <title>Anime Character Sprite - Explorez l'univers de l'anime</title>
  </head>
</template>
