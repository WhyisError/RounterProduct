<template>
  <v-container>
    <v-card max-width="500" class="mx-auto">
      <v-toolbar color="indigo" dark>
        <v-app-bar-nav-icon></v-app-bar-nav-icon>

        <v-toolbar-title>Inbox</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-toolbar>
      <v-list>
        <v-list-item v-for="(item, index) in productDetail" :key="index">
          <v-list-item-content>
            <v-list-item-title v-text="item.name"></v-list-item-title>
          </v-list-item-content>
          <v-list-item-content>
            <v-list-item-title v-text="item.price"></v-list-item-title>
          </v-list-item-content>
          <v-list-item-content>
            <v-list-item-title v-text="item.quantity"></v-list-item-title>
          </v-list-item-content>

          <v-btn>Delete</v-btn>
        </v-list-item>
      </v-list>
    </v-card>
   
    <br>
    <div>
        Product Id : {{this.$route.params.id}} quantity : {{slider}}
    </div>
    <v-card flat color="transparent">
      <v-subheader>Min and max default slider</v-subheader>

      <v-card-text>
        <v-row>
          <v-col class="pr-4">
            <v-slider
              v-model="slider"
              class="align-center"
              :max="10"
              :min="1"
              hide-details
            >
              <template v-slot:append>
                <v-text-field
                  v-model="slider"
                  class="mt-0 pt-0"
                  hide-details
                  single-line
                  type="number"
                  style="width: 60px"
                ></v-text-field>
              </template>
            </v-slider>
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>
    <v-btn @click="add">Add</v-btn>
  </v-container>
</template>

<script>
export default {
  props: {
    details: Array,
  },
  data: () => ({
    i: 0,
    id:0,
    min: 1,
    max: 10,
    slider: 1,
    productDetail: [
     
    ],
  }),
  methods: {
    add() {
        this.id = this.$route.params.id;
        for(this.i in this.details){
            if(this.id == this.details[this.i].id){
                this.productDetail.push({
                    name:this.details[this.i].name,
                    price:this.details[this.i].price,
                    quantity:this.slider
                });
            }
        }
    },
  },
};
</script>

<style></style>