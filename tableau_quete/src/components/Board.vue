<script>
import Col from './Col.vue' //Importation du composant Col

export default{
  components:{Col},  // Déclaration du composant Col

  data(){ 
    return{
      etapes:[
        {nom:"À faire",statut:"À faire"},
        {nom:"En cours",statut:"En cours"},
        {nom:"Terminé",statut:"Terminé"}
      ], // Liste des étapes de la quête
      listeQuetes:[] // Liste des quêtes
    }
  },

  created(){ // Récupération des quêtes depuis le localStorage
    let save = localStorage.getItem("quetes")
    if(save) this.listeQuetes = JSON.parse(save)
  },

  computed:{ // Calcul des quêtes triées par statut
    quetesTriees(){
      let res = {}
      this.etapes.forEach(e => {
        res[e.statut] = this.listeQuetes.filter(q => q.statut === e.statut)
      })
      return res
    }
  },

  watch:{ // Surveillance des changements dans la liste des quêtes pour les sauvegarder dans le localStorage
    listeQuetes:{
      handler(v){ // Sauvegarde des quêtes dans le localStorage
        localStorage.setItem("quetes",JSON.stringify(v))
      },
      deep:true
    }
  },

  methods:{
    ajouterQuete(q){  // Ajouter une nouvelle quête à la liste des quêtes
      this.listeQuetes.push({
        id:Date.now(),
        nom:q.nom,
        rang:q.rang,
        statut:"À faire", // Statut initial de la quête
        recompense:q.recompense
      })
    },

    changerStatut(id,statut){ // Changer le statut d'une quête
      let q = this.listeQuetes.find(x => x.id === id)
      if(q) q.statut = statut
    },

    avancerQuete(id){ // Avancer le statut d'une quête
      let q = this.listeQuetes.find(x => x.id === id)
      if(!q) return

      if(q.statut === "À faire") q.statut = "En cours"
      else if(q.statut === "En cours") q.statut = "Terminé"
    },

    reculerQuete(id){  // Reculer le statut d'une quête
      let q = this.listeQuetes.find(x => x.id === id)
      if(!q) return

      if(q.statut === "Terminé") q.statut = "En cours"
      else if(q.statut === "En cours") q.statut = "À faire"
    }
  }
}
</script>

<template>
  <div class = "board"> 
    <Col v-for = "e in etapes" :key = "e.statut" :titre = "e.nom" :statut = "e.statut" :quetes = "quetesTriees[e.statut]"
      @changerStatut = "changerStatut" 
      @avancerQuete = "avancerQuete"
      @reculerQuete = "reculerQuete"
    /> <!-- Composant Col pour chaque étape de la quête -->
  </div>
</template>

<style>
</style>