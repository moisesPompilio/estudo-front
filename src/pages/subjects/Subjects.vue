<template>
  <main>
    <v-parallax width="100%" height="100%" src="https://cdn.vuetifyjs.com/images/parallax/material.jpg">
      <article>

        <v-card id="menu">
          <v-row id="title">
            <h1>ESTABLISHEDS-META</h1>
          </v-row>
          <v-row id="filter">
            <v-col sm="4">
              <v-text-field placeholder="Filter by name" />
            </v-col>
            <v-col sm="4" id="col-add">
              <MyButton id="button-add" primary size="medium" @onClick="edit = true, editIten = {}" label="ADD META" color="#ffffff" />
            </v-col>
            <v-col sm="4">
              <v-text-field dense placeholder="Filter by decription" />
            </v-col>
          </v-row>
        </v-card>
        <div id="metas" v-for="meta of metasItens" :key="meta.id">
          <v-card class="meta-iten">
            <v-row>
              <h2>{{ meta.titulo }}</h2>
            </v-row>
            <v-row>
              <p>{{ meta.descricao }}</p>
            </v-row>
            <v-row>
              <h3>Study hours: {{ meta.horasEstudo }}h</h3>
            </v-row>
            <v-row class="buttons-meta">
              <v-col cols="12" sm="6" md="3">
                <MyButton class="button" primary size="medium" @onClick="onLogout" label="Study" color="#ffffff" />
              </v-col>
              <v-col cols="12" sm="6" md="3">
                <MyButton class="button" size="medium" @onClick=" editar(meta)" label="To edit" color="#38B6FF" />
              </v-col>
            </v-row>
          </v-card>
        </div>
      </article>
      <MyEdit :itens="editIten" v-if="edit" @closeEdit="edit = false" @editar="editar"/>
    </v-parallax>
  </main>
</template>

<script>
import "./Subjects.css";
import MyButton from "@/components/comuns/Button.vue";
import MyEdit from "@/components/complexity/EditModulos.vue";
import Cookies from "js-cookie";
export default {
  name: "subjects",
  components: { MyButton , MyEdit },
  setup() { },
  data(
  ) {
    return {
      more: false,
      edit: false,
      editIten: {},
      propsEdit: {},
      metasItens: [
        {
          id: "1",
          horasEstudo: 10.5,
          asunto: "Asunto",
          descricao:
            "It is often said and rarely true that a particular novel defies classification or even description. Such however seems truth-fully to be the case with Vladimir Nabokov* s LOLITA. It has been called everything from “a strong, a disturbing book” (The Manchester Guardian) and “a distinguished novel” (Graham Greene)",
        },
        {
          id: "2",
          horasEstudo: 10.5,
          titulo: "Asunto",
          descricao:
            "It is often said and rarely true that a particular novel defies classification or even description. Such however seems truth-fully to be the case with Vladimir Nabokov* s LOLITA. It has been called everything from “a strong, a disturbing book” (The Manchester Guardian) and “a distinguished novel” (Graham Greene)",
        },
        {
          id: "3",
          horasEstudo: 10.5,
          asunto: "Asunto",
          descricao:
            "It is often said and rarely true that a particular novel defies classification or even description. Such however seems truth-fully to be the case with Vladimir Nabokov* s LOLITA. It has been called everything from “a strong, a disturbing book” (The Manchester Guardian) and “a distinguished novel” (Graham Greene) It is often said and rarely true that a particular novel defies classification or even description. Such however seems truth-fully to be the case with Vladimir Nabokov* s LOLITA. It has been called everything from “a strong, a disturbing book” (The Manchester Guardian) and “a distinguished novel” (Graham Greene)",
        },
        {
          id: "4",
          horasEstudo: 10.5,
          asunto: "Asunto",
          descricao:
            " Such however seems truth-fully to be the case with Vladimir Nabokov* s LOLITA. It has been called everything from “a strong, a disturbing book” (The Manchester Guardian) and “a distinguished novel” (Graham Greene)",
        },
      ],
    };
  },
  methods: {
    async editar(iten){
      this.edit = true;
      this.editIten = iten;
    }
  },
};
</script>