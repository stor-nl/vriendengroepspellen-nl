---
layout: default
title: Standard Games
permalink: /standaard/
---

<section class="max-w-7xl mx-auto py-6">
  <div class="flex flex-col md:flex-row justify-between">

    <!-- Sidebar -->
    <aside class="w-full md:w-1/4 md:mr-6 mb-6 md:mb-0">
      <div class="mb-6">
        <h2 class="text-xl font-bold mb-2">Zoek spellen</h2>
        <input type="text" id="searchInput" placeholder="Zoek spellen..." class="border p-2 w-full mb-4">
      </div>

      <div class="mb-6">
        <h2 class="text-xl font-bold mb-2">Spelers</h2>
        <div class="flex space-x-2 mb-4">
          <div class="w-1/2">
            <label for="minPlayers" class="block font-medium">Minimaal:</label>
            <input type="number" id="minPlayers" class="border p-2 w-full" min="1" placeholder="1">
          </div>
          <div class="w-1/2">
            <label for="maxPlayers" class="block font-medium">Maximaal:</label>
            <input type="number" id="maxPlayers" class="border p-2 w-full" min="1" placeholder="10">
          </div>
        </div>
      </div>

      <div class="mb-6">
        <h2 class="text-xl font-bold mb-2">Type</h2>
        <div id="typeFilter" class="flex flex-wrap gap-2">
          <!-- Type buttons will be dynamically inserted here by JavaScript -->
        </div>
      </div>
    </aside>

    <!-- Posts List -->
    <div class="w-full md:w-3/4">
      <ul id="gamesList" class="space-y-6">
        {% for post in site.posts %}
        <li class="bg-white shadow-lg rounded-lg overflow-hidden transition-transform transform hover:scale-105"
            data-min-players="{{ post.min-players }}" data-max-players="{{ post.max-players }}" data-type="{{ post.type }}">
          <a href="{{ post.url | relative_url }}" class="block p-6">
            <h3 class="text-xl font-semibold mb-2">{{ post.title }}</h3>
            <p class="text-gray-700">{{ post.subtitle }}</p>
            <div class="mt-4 space-x-2">
                <span class="bg-blue-200 text-blue-800 px-2 py-1 rounded">{{ post.type }}</span>
                <span class="bg-blue-200 text-blue-800 px-2 py-1 rounded">{{ post.min-players }} - {{ post.max-players }} spelers</span>    
            </div>
          </a>
        </li>
        {% endfor %}
      </ul>
    </div>

  </div>
</section>

<script>
  var activeTypes = [];

  // Populate the type filter dynamically based on post types
  document.addEventListener('DOMContentLoaded', function() {
    var types = new Set();
    var items = document.querySelectorAll('#gamesList li');
    
    items.forEach(function(item) {
      types.add(item.getAttribute('data-type'));
    });

    var typeFilterDiv = document.getElementById('typeFilter');
    types.forEach(function(type) {
      var button = document.createElement('button');
      button.className = 'bg-green-200 text-green-800 px-3 py-1 rounded hover:bg-green-300 active:bg-green-400';
      button.textContent = type;
      button.style.flex = '0 1 auto'; // Ensure all buttons have the same size
      button.onclick = function() { toggleTypeFilter(button, type); };
      typeFilterDiv.appendChild(button);
    });
  });

  document.getElementById('minPlayers').addEventListener('input', function() {
    filterPosts();
  });

  document.getElementById('maxPlayers').addEventListener('input', function() {
    filterPosts();
  });

  document.getElementById('searchInput').addEventListener('keyup', function() {
    filterPosts();
  });


  function toggleTypeFilter(button, type) {
    if (button.classList.contains('bg-green-400')) {
      button.classList.remove('bg-green-400', 'text-white');
      button.classList.add('bg-green-200', 'text-green-800');
      activeTypes = activeTypes.filter(t => t !== type);
    } else {
      button.classList.remove('bg-green-200', 'text-green-800');
      button.classList.add('bg-green-400', 'text-white');
      activeTypes.push(type);
    }
    filterPosts();
  }

  function filterPosts() {
    var searchFilter = document.getElementById('searchInput').value.toUpperCase();
    var minPlayersFilter = parseInt(document.getElementById('minPlayers').value) || 0;
    var maxPlayersFilter = parseInt(document.getElementById('maxPlayers').value) || Infinity;

    var list = document.getElementById('gamesList');
    var items = list.getElementsByTagName('li');

    for (var i = 0; i < items.length; i++) {
      var item = items[i];
      var text = item.textContent || item.innerText;
      var minPlayers = parseInt(item.getAttribute('data-min-players')) || 0;
      var maxPlayers = parseInt(item.getAttribute('data-max-players')) || Infinity;
      var type = item.getAttribute('data-type');

      var matchesSearch = text.toUpperCase().indexOf(searchFilter) > -1;
      var matchesPlayers = minPlayers >= minPlayersFilter && maxPlayers <= maxPlayersFilter;
      var matchesType = activeTypes.length === 0 || activeTypes.includes(type);

      if (matchesSearch && matchesPlayers && matchesType) {
        item.style.display = "";
      } else {
        item.style.display = "none";
      }
    }
  }
</script>
