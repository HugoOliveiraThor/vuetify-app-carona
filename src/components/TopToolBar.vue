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
        <v-row>
          <v-col>
            <v-expansion-panels>
              <v-expansion-panel v-for="(item,i) in list" :key="i">
                <v-expansion-panel-header>{{item.name}}</v-expansion-panel-header>
                <v-expansion-panel-content>
                  <contentUser :form="item" />
                </v-expansion-panel-content>
              </v-expansion-panel>
            </v-expansion-panels>
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
import contentUser from './Content'
export default {
  name: "LayoutsDemosBaselineFlipped",
  components: {
    contentUser
  },
  props: {
    source: String
  },
  data: () => ({
    drawer: null,
    form: {},
    menu: "",
    list: [
      { name: "Hugo Oliveira", date: new Date() },
      { name: "Alex Silva", date: new Date() },
      { name: "Irwing", date: new Date() },    
    ]
  })
};
</script>