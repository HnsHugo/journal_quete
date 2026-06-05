<script setup></script>

<template>
  <div class="app" id="app">
     <header class="header">
        <div class="header-left">
          <img src="/logo.png" alt="Logo" class="logo" href="/"/>
        </div>

        <div class="header-center">
          <h1>Tableau des quêtes</h1>
        </div>

        <div class="header-right">
          <button class="add-quest-button">
            Ajouter une quête
          </button>
        </div>
      </header>

    
    <table class="quest-table">
      <thead>
        <tr>
          <th>Quête</th>
          <th>Rang</th>
          <th>Statut</th>
          <th>Récompense</th>
        </tr>
      </thead>

      <tbody>
        <tr>
          <td>Dire bonjour à la voisine qui gueule à chaque soirée</td>
          <td>S</td>
          <td>Terminé</td>
          <td>+100 XP</td>
        </tr>
        <tr>
          <td>Faire la vaisselle</td>
          <td>C</td>
          <td>Terminé</td>
          <td>+20 XP</td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<style src="./assets/style.css"></style>
