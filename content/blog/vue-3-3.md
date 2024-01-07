---
title: Annonce de Vue 3.3
description: Cette version est axée sur l'amélioration de l'expérience des développeurs et la correction de bogues.
date: 2023-12-24
cover: 333.jpg
tags:
  - vue
---

# Annonce de Vue 3.3

Aujourd'hui, nous sommes ravis d'annoncer la sortie de Vue 3.3 "Rurouni Kenshin" !

Cette version se concentre sur l'amélioration de l'expérience des développeurs, en particulier l'utilisation de SFC `<script setup>` avec TypeScript. En collaboration avec la version 1.6 de Vue Language Tools (anciennement connue sous le nom de Volar), nous avons résolu de nombreux problèmes persistants lors de l'utilisation de Vue avec TypeScript.

Cet article offre un aperçu des fonctionnalités phares de la version 3.3. Pour la liste complète des changements, veuillez consulter le journal des modifications complet sur GitHub.

## `<script setup>` + Améliorations de l'expérience de développement TypeScript

### Prise en charge des types importés et complexes dans les Macros

Auparavant, les types utilisés dans la position du paramètre de type de defineProps et defineEmits étaient limités aux types locaux et prenaient en charge uniquement les littéraux de type et les interfaces. Cela est dû au besoin de Vue d'analyser les propriétés de l'interface des props afin de générer les options d'exécution correspondantes.

Cette limitation est maintenant résolue dans la version 3.3. Le compilateur peut désormais résoudre les types importés et prend en charge un ensemble limité de types complexes :

```vue
<script setup lang="ts">
import type { Props } from "./foo";

// type importé + type intersection
defineProps<Props & { extraProp?: string }>();
</script>
```

Veuillez noter que la prise en charge des types complexes est basée sur l'AST et n'est donc pas exhaustive à 100 %. Certains types complexes qui nécessitent une analyse de type réelle, par exemple les types conditionnels, ne sont pas pris en charge. Vous pouvez utiliser des types conditionnels pour le type d'une seule prop, mais pas pour l'ensemble de l'objet props.
