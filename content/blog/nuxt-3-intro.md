---
title: Démarrer avec Nuxt 3
description: Ceci est une introduction rapide sur la manière de commencer avec Nuxt 3. Ainsi que construire son app.vue
date: 2023-12-24
cover: nux2.jpg
tags:
  - nuxt
  - vue
---

# Démarrer avec Nuxt 3

Ceci est une brève introduction sur la manière de commencer avec Nuxt 3. Pour commencer, vous devez avoir Node.js installé sur votre machine. Vous pouvez le télécharger [ici](https://nodejs.org/en/download/). Une fois Node.js installé, vous pouvez installer Nuxt 3 en utilisant la commande suivante :

```bash
npx nuxi init <nom-du-projet>
cd <nom-du-projet>
npm i
```

Ensuite, vous pouvez commencer à construire votre application en utilisant `app.vue`.


```vue
<script setup></script>

<template>
  <div class="flex flex-col min-h-screen">
    <SiteHeader />
    <main class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8 grow items-start w-full">
      <NuxtPage />
    </main>
    <SiteFooter />
  </div>
</template>
```
