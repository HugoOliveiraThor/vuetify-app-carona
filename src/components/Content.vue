<template>
    <v-row align="center" justify="center">
        {{form}}
          <v-col class="text-center">
            <v-row align="center">
              <v-row justify="space-around">
                <v-col cols="12" sm="6">
                  <v-col cols="12" sm="6" md="4">
                    <v-menu
                      ref="menu"
                      v-model="menu"
                      :close-on-content-click="false"
                      :return-value.sync="form.date"
                      transition="scale-transition"
                      offset-y
                      min-width="290px"
                    >
                      <template v-slot:activator="{ on }">
                        <v-text-field
                             v-model="form.date" 
                             label="Data da carona" 
                             readonly 
                             v-on="on">
                        </v-text-field>
                      </template>
                      <v-date-picker 
                        v-model="form.date" 
                        no-title scrollable>
                        <v-spacer></v-spacer>
                        <v-btn 
                            text 
                            color="primary" 
                            @click="menu = false">
                            Cancel
                        </v-btn>
                        <v-btn 
                            text color="primary" 
                            @click="$refs.menu.save(date)">
                            OK
                        </v-btn>
                      </v-date-picker>
                    </v-menu>
                  </v-col>
                </v-col>
                <v-switch 
                    v-model="form.ida" 
                    class="ma-2" 
                    label="Ida">
                </v-switch>
                <v-switch 
                    v-model="form.volta" 
                    class="ma-2" 
                    label="Volta">
                </v-switch>
              </v-row>
              <v-divider></v-divider>
            </v-row>
          </v-col>
        </v-row>
</template>

<script>
    export default {
        name:'Content',
        props: ['form'],
        mounted() {
            console.log('this.form;', this.form)
        },
        data() {
            return {}
        }
    }
</script>

<style lang="scss" scoped>

</style>