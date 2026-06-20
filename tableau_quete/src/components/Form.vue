<script>
export default{
  emits:['ajouterQuete','fermerForm'], // Déclaration des événements émis par le composant Form
  data(){
    return{nouvelleQuete:{nom:'',rang:'',recompense:''}} 
  },
  methods:{ // Méthode pour valider le formulaire et émettre l'événement ajouterQuete
    validerFormulaire(){
      let q = this.nouvelleQuete
      if(q.nom.trim() === ""){
        alert("Le nom de la quête est requis.")
        return
      }
      this.$emit('ajouterQuete',{nom:q.nom,rang:q.rang,recompense:q.recompense})
      this.nouvelleQuete = {nom:'',rang:'',recompense:''}
    }
  }
}
</script>

<template>
  <div class = "modal-overlay">
    <div class = "quest-modal">
      <h1>Ajouter une quête</h1>
      <form @submit.prevent = "validerFormulaire"> <!-- Formulaire pour ajouter une nouvelle quête -->
        <label>Nom de la quête</label><input type = "text" v-model = "nouvelleQuete.nom" required>
        <label>Rang de la quête</label>
        <select v-model = "nouvelleQuete.rang" required>
          <option value = "D">D</option>
          <option value = "C">C</option>
          <option value = "B">B</option>
          <option value = "A">A</option>
          <option value = "S">S</option>
        </select>
        <label>Récompense</label><input type = "text" v-model = "nouvelleQuete.recompense" required>
        <div class = "modal-buttons">
          <button type = "button" class = "modal-cancel" @click = "$emit('fermerForm')" >Annuler</button>
          <button type = "submit" class = "modal-ok" >Ajouter</button>
        </div>
      </form>
    </div>
  </div>
</template>

<style>
</style>