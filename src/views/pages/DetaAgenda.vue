<template>
  <v-container fluid class="down-top-padding">
     <!--esta es la page es de mi perfil(jesus)-->
      <v-col>
        <v-card>
          <v-card-text>
            <h3 class="title blue-grey--text text--darken-2 font-weight-regular">Detalles Agenda</h3>
            <h6 class="subtitle-2 font-weight-light">Esta seccion es ver a detalle una agenda</h6>
          </v-card-text>
          <v-card-text>
            <p>ID: {{ result.id }}</p>
            <p>fecha inical: {{ result.dtDiaAgenda }}</p>
            <p>fecha limite: {{ result.dtFechaCuidar }}</p>
            <p>Hora: {{ result.hora }}</p>
            <p>Tarea: {{ result.strDescripcion }}</p>
                        <v-card-text>
                            <h3 class="title blue-grey--text text--darken-2 font-weight-regular">Pedido #1028</h3>
                        </v-card-text>
                        
                        <v-alert
                        border="left"
                        color="indigo"
                        dark
                        >
                            Estado: Pendiente
                        </v-alert>
          </v-card-text>
           <v-row align="center" justify="space-around">
      <v-btn
        tile
        color="success"
        @click="regreso"
      >
        <v-icon left>
          mdi-arrow-left-bold-circle
        </v-icon>
        Regresar
      </v-btn>
    </v-row>
        </v-card>
      </v-col>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    result: null
  }),
  created() {
    axios.get("https://apipet18301044.herokuapp.com/agendar/"+this.$route.query.id).then((result) => {
      this.result = result.data;
    })
},
 methods: {
    regreso(){
                this.$router.push(`/pages/alerts`);
            },
  },
};
</script>