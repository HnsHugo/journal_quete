<script>
import Board from './components/Board.vue' // Importation des composants 
import Form from './components/Form.vue'

export default{
  components:{Board,Form},
  data(){
    return{afficherModal:false}
  },
  methods:{ // Méthodes pour l'affichage
    ouvrirModal(){
      this.afficherModal = true
    },
    fermerModal(){
      this.afficherModal = false
    },
    ajouterDepuisForm(q){ // Ajouter une quête
      this.$refs.board.ajouterQuete(q)
      this.fermerModal()
    }
  }
}
</script>

<template>
  <div class = "app" id = "app">
    <header class = "header">  <!-- Header de l'application avec le logo, le titre et le bouton pour ajouter une quête-->
      <div class = "header-left">
        <img src = "/logo.png" alt = "Logo" class = "logo">
      </div>

      <div class = "header-center">
        <h1>Tableau des quêtes</h1>
      </div>

      <div class = "header-right">
        <button class = "add-quest-button" @click = "ouvrirModal">Ajouter une quête</button>
      </div>
    </header>

    <Board ref = "board"/> <!-- Composant Board pour afficher les quêtes -->

    <Form 
      v-if = "afficherModal"
      @fermerForm = "fermerModal"
      @ajouterQuete = "ajouterDepuisForm"
    /> <!-- Composant Form pour ajouter une nouvelle quête -->
  </div>
</template>

<style src = "./assets/style.css"></style> <!--Lien css-->