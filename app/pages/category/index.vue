<template>
  <v-container fluid>
    <v-card title="Category" flat elevation="2">
      <template v-slot:text>
        <v-text-field
          v-model="search"
          label="Search"
          prepend-inner-icon="mdi-magnify"
          variant="outlined"
          hide-details
          single-line
        ></v-text-field>
      </template>

      <v-data-table
        :headers="headers"
        :items="category.data"
        :search="search"
      ></v-data-table>
    </v-card>
  </v-container>
</template>

<script setup>
const { data: category, error } = await useFetch(
  "http://localhost:1337/api/categories"
);
// console.log(category.data);
const search = ref("");

const headers = [
  { key: "category_name", title: "Product Name" },
  { key: "description", title: "Description" },
  { key: "createdAt", title: "Created At" },
];
</script>

<style></style>
