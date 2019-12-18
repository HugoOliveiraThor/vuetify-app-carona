<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app right>
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title>Controle diário</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-contact-mail</v-icon>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title>Controle mensal</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="cyan" dark>
      <v-spacer />
      <v-toolbar-title>Carona</v-toolbar-title>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
    </v-app-bar>

    <v-content>
      <v-container fluid>
        <v-row align="center" justify="center">
          {{dayOfTheWeek}}
        </v-row>
        <v-row align="center" justify="center">
          {{formatDate}}
        </v-row>
        <v-row dense>
        <v-col
          v-for="(item, i) in list"
          :key="i"
          cols="12"
        >
          <v-card>
            <v-row>
              <v-col cols="6">
              <div class="d-flex flex-no-wrap justify-space-between">
                <v-card-subtitle v-text="item.name"></v-card-subtitle>
              </div>
            </v-col>
            <v-col cols="6" class="text-center">
              <v-btn 
                color="primary"
                @click="() => register(item)"  
              >Adicionar</v-btn>
            </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
      </v-container>
    </v-content>

    <v-footer color="cyan" app>
      <v-spacer />

      <span class="white--text">&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
// import contentUser from './Content'
import moment from 'moment'
moment.locale('pt-br')
export default {
  name: "LayoutsDemosBaselineFlipped",
  // components: {
  //   contentUser
  // },
  props: {
    source: String
  },
  computed: {
    formatDate () {
      return moment().format('DD/MM/YYYY') 
    },
    dayOfTheWeek () {
      return moment(new Date(), "D_M_YYYY").locale('pt-br').format('dddd')
    }
  },
  mounted() {
    // let v = localStorage.getItem('hugo')
    // if(localStorage.getItem('corridas')) {

    // }
    // console.log('v', v)
  },
  data: () => ({
    drawer: null,
    form: {},
    menu: "",
    list: [
      { id: 1, name: "Hugo Oliveira", date: moment().format('LLL') },
      { id: 2, name: "Alex Silva", date: moment().toDate() },
      { id: 3 , name: "Irwing", date: moment().toDate() },    
    ],
    actualDate:''
  }),
  methods: {
    register(register) {
      this.verifyConditionToAdd(register)
      console.log('Registrou', register)
    },
    verifyConditionToAdd (register) {
      if(localStorage.getItem('corridas')) {
        let u = localStorage.getItem('corridas')
        console.log('u', u)
      } else {
        console.log('Entrou', JSON.stringify(register))
        localStorage.setItem('corridas', JSON.stringify(register))
      }
    }
  }
};
</script>