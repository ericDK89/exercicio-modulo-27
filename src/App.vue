<script setup lang="ts">
import { reactive } from "vue";

const state = reactive({
  a: 0,
  b: 0,
  function: "sum",
  result: 0,
  isValid: false,
});

const calc = () => {
  switch (state.function) {
    case "minus":
      state.result = state.a - state.b;
      return state.result;

    case "times":
      state.result = state.a * state.b;
      return state.result;

    case "divide":
      state.result = state.a / state.b;
      return state.result;

    default:
      state.result = state.a + state.b;
      return state.result;
  }
};
</script>

<template>
  <div class="bg-dark vh-100">
    <div
      class="container w-50 py-5 position-absolute top-50 start-50 translate-middle"
    >
      <form @submit.prevent="calc()" class="bg-primary p-3 rounded-3">
        <div class="d-flex">
          <div class="row">
            <div>
              <label class="text-white" for="1">Valor 1: </label>
              <input
                class="form-control"
                type="number"
                id="1"
                @change="(e) => state.a = Number((e.target as HTMLInputElement).value)"
                v-model="state.a"
                @input="calc()"
              />
            </div>

            <div class="mt-3">
              <label class="text-white" for="2">Valor 2: </label>
              <input
                class="form-control"
                type="number"
                id="2"
                @change="(e) => state.b = Number((e.target as HTMLInputElement).value)"
                v-model="state.b"
                @input="calc()"
              />
            </div>
          </div>

          <div class="row align-items-center ms-5">
            <select
              class="form-select"
              @change="(e) => state.function = (e.target as HTMLSelectElement).value"
            >
              <option value="sum">Soma</option>
              <option value="minus">Subtração</option>
              <option value="times">Multiplicação</option>
              <option value="divide">Divisão</option>
            </select>
          </div>

          <p
            class="text-white text-center h3 mt-5 text-decoration-underline ms-5"
          >
            Resultado: {{ state.result }}
          </p>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped></style>
