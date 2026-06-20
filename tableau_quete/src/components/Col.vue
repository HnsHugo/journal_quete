<script>
import Quete from './Quete.vue' // Importation du composant Quete

export default{
  components:{Quete}, // Déclaration du composant Quete
  props:{ // Déclaration des props du composant Col
    titre:String,
    quetes:Array
  },
  emits:['changerStatut','avancerQuete','reculerQuete']  // Déclaration des événements émis par le composant Col
}
</script>

<template>
  <div class = "col">
    <h1>{{ titre }}</h1>
    <Quete
      v-for = "q in quetes" 
      :key = "q.id"
      :quete = "q"
      @changerStatut = "$emit('changerStatut',$event)"
      @avancerQuete = "$emit('avancerQuete',$event)"
      @reculerQuete = "$emit('reculerQuete',$event)"
    />  <!-- Boucle pour afficher les quêtes dans chaque étape -->
  </div>
</template>

<style>
</style>