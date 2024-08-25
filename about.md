---
layout: default
title: Over Ons
---

<section class="bg-gray-100 py-12">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <h2 class="text-4xl font-extrabold text-gray-900 mb-4 text-center">Over Ons</h2>
    <p class="text-lg text-gray-700 mb-8 text-center">
      Vriendengroepspellen is een website opgericht door twee vrienden uit de omgeving van Amsterdam. Wij maken deel uit van een vriendengroep die ontzettend van spellen houdt, vooral eenvoudige kaart- en dobbelspellen die vaak gepaard gaan met drinken. Om ervoor te zorgen dat we de regels niet vergeten en om onze spellen met de wereld te delen, hebben we besloten om deze website te creëren. Daarnaast willen we premium spellen maken die voor elke prijs gekocht kunnen worden, deze zijn momenteel in ontwikkeling.
    </p>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-12 mb-12">
      <!-- Yoran Hoek Section -->
      <div class="text-center">
        <img src="/assets/img/yoran-hoek.webp" alt="Yoran Hoek" class="w-48 h-48 mx-auto rounded-full mb-4">
        <h3 class="text-2xl font-bold text-gray-900">Yoran Hoek</h3>
      </div>
      <!-- Tijmen Stor Section -->
      <div class="text-center">
        <img src="/assets/img/tijmen-stor.webp" alt="Tijmen Stor" class="w-48 h-48 mx-auto rounded-full mb-4">
        <h3 class="text-2xl font-bold text-gray-900">Tijmen Stor</h3>
      </div>
    </div>
    <h3 class="text-3xl font-bold text-gray-900 mb-6 text-center">Neem Contact Op</h3>
    <p class="text-lg text-gray-700 mb-8 text-center">
      Heb je vragen, opmerkingen of suggesties? Neem dan gerust contact met ons op via onderstaand contactformulier.
    </p>
    <!-- Contact Form -->
    <div class="max-w-xl mx-auto">
      <form action="https://formspree.io/f/YOUR_FORMSPREE_ENDPOINT" method="POST">
        <div class="mb-4">
          <label for="name" class="block text-lg font-medium text-gray-700">Naam</label>
          <input type="text" id="name" name="name" class="border p-2 w-full rounded" required>
        </div>
        <div class="mb-4">
          <label for="email" class="block text-lg font-medium text-gray-700">E-mail</label>
          <input type="email" id="email" name="_replyto" class="border p-2 w-full rounded" required>
        </div>
        <div class="mb-4">
          <label for="message" class="block text-lg font-medium text-gray-700">Bericht</label>
          <textarea id="message" name="message" class="border p-2 w-full rounded h-32" required></textarea>
        </div>
        <div class="text-center">
          <button type="submit" class="bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-6 rounded-lg">Verstuur</button>
        </div>
      </form>
    </div>
  </div>
</section>
