<template>
  <Container>
    <h1 class="text-5xl font-bold mt-20">Contact</h1>
    <br>
    <!-- Bloc indépendant en dessous du formulaire -->
<div class="grid grid-cols-1 md:grid-cols-3 gap-4 mt-8">
  <!-- Colonne 1 : Adresse e-mail -->
  <div class="bg-gray-200 p-4 rounded-lg">
    <label class="block text-gray-700 mb-2 font-bold" for="email">
      Adresse E-mail
    </label>
    <p class="text-black">antoine.remacle@ifosup.wavre.be</p>
  </div>

  <!-- Colonne 2 : Téléphone -->
  <div class="bg-gray-200 p-4 rounded-lg">
    <label class="block text-gray-700 mb-2 font-bold" for="phone">
      Téléphone
    </label>
    <p class="text-black">+123 456 789</p>
  </div>

  <!-- Colonne 3 : Emplacement -->
  <div class="bg-gray-200 p-4 rounded-lg">
    <label class="block text-gray-700 mb-2 font-bold" for="location">
      Emplacement
    </label>
    <p class="text-black">Wavre, Belgique</p>
  </div>
</div>
<br><br>
<h2 class="text-3xl font-bold mb-4 mt-3">Formulaire</h2>
<hr class="mt-3 border-t-4 border-blue-400 w-40">
<br><br>
    <form action="#" class="mb-12">
      <div class="flex flex-wrap mb-6 -mx-4">
        <div class="w-full md:w-1/2 mb-6 md:mb-0 px-4">
          <label class="block mb-2 text-copy-primary" for="name">
            Name
          </label>
          <input
            type="text"
            name="name"
            id="name"
            placeholder="Jhon Cena"
            class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none focus:border-green-700 mb-2 p-4 text-black"
            required
          />
        </div>

        <div class="w-full px-4 md:w-1/2">
          <label class="block text-copy-primary mb-2" for="email">
            Email Address
          </label>
          <input
            type="email"
            name="email"
            id="email"
            placeholder="email@example.com"
            class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none focus:border-green-700 mb-2 p-4 text-black"
            required
          />
        </div>
      </div>

      <div class="w-full mb-12">
        <label class="block text-copy-primary mb-2" for="message">
          Message
        </label>
        <textarea
          id="message"
          rows="5"
          name="message"
          class="block w-full bg-background-form border border-border-color-primary shadow rounded outline-none appearance-none focus:border-green-700 mb-2 px-4 py-4 text-black"
          placeholder="Enter your message here."
          required
        ></textarea>
      </div>

      <div class="flex justify-start w-full">
        <div>
          <input
            type="submit"
            value="Submit"
            class="block bg-sky-700 hover:bg-sky-800 text-white text-sm font-semibold tracking-wide uppercase shadow rounded cursor-pointer px-6 py-3"
            @click="afficherMessageErreur"
          />
          <p v-if="erreur" class="text-red-500 mt-2">Formulaire non fonctionnel.</p>
        </div>
      </div>
    </form>
    <br><br>
  </Container>
</template>

<script>
export default {
  data() {
    return {
      erreur: false,
    };
  },
  methods: {
    afficherMessageErreur() {
      this.erreur = true;
    },
  },
};
</script>