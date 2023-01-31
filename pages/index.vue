<template>
  <div class="p-4">
    <nav class="flex justify-between">
      <h1>Pet Canager 3000</h1>
      <div class="">
        <span>Dog Name</span>
        <input v-model="add" class="border-2 border-gray-200" type="text" />
        <button @click="() => listedsDog()">Add pet</button>
      </div>
    </nav>
    <main class="gap-2 flex justify-around">
      <div class="border-2 border-black w-[33%] min-h-[30px]">
        <div class="w-full">Listed</div>
        <div v-for="(listed, index) in listeds" :key="listed + index">
          {{ listed }}
          <button @click="examingsDog(index)">Next</button>
        </div>
      </div>
      <div class="border-2 border-black w-[33%] min-h-[30px]">
        <div class="w-full">Examining</div>
        <div v-for="(examing, indeccc) in examings" :key="examing + indeccc">
          {{ examing }}
          <button @click="backHumansDog(indeccc)">Next</button>
        </div>
      </div>
      <div class="border-2 border-black w-[33%] min-h-[30px]">
        <div class="w-full">Finally Back to Hooman</div>
        <div
          v-for="(backHuman, inde22) in backHumans"
          :key="backHuman + inde22"
        >
          {{ backHuman }}
        </div>
      </div>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const add = ref("");

const listeds = ref([]);
const examings = ref([]);
const backHumans = ref([]);

const listedsDog = () => {
  listeds.value.push(add.value);
  add.value = "";
};

const examingsDog = (index) => {
  examings.value.push(listeds.value[index]);
  listeds.value.splice(index, 1);
};

const backHumansDog = (index) => {
  backHumans.value.push(examings.value[index]);
  examings.value.splice(index, 1);
};
</script>
