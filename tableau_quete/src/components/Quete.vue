<script>
export default {
  props: { // Déclaration des props du composant Quete
    quete: Object
  },
  emits: ['changerStatut', 'avancerQuete', 'reculerQuete'] // Déclaration des événements émis par le composant Quete
};
</script>
<template>
  <div class="quest-card"> <!-- Carte de la quête avec les informations et les boutons pour avancer ou reculer le statut -->
    <h2>{{ quete.nom }}</h2>
    <p>Rang: {{ quete.rang }}</p>
    <p>Statut: {{ quete.statut }}</p>
    <p>Récompense: {{ quete.recompense }}</p>
    <div class = "quest-button">
      <button class = "back-button" v-if = "quete.statut !== 'À faire'" @click = "$emit('reculerQuete', quete.id)"> Reculer </button>
      <button class = "next-button" v-if = "quete.statut !== 'Terminé'" @click = "$emit('avancerQuete', quete.id)"> Avancer </button>

    </div>
  </div>
</template>
<style>
</style>