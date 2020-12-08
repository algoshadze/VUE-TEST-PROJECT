<template>
  <div class="pad">
    <ul>
      <li v-for="(s, i) of statuses" :key="s">
        <br />
        <span v-if="i > 0" class="or"> или</span> Статус&nbsp;{{ i + 1 }}
        <select
          @change="selectionChange"
          v-model="statuses_prop[i]"
          class="sel"
        >
          <option v-for="st of statusTypes" :key="st">{{ st }}</option>
        </select>
      </li>
      <br />
    </ul>
    <button @click="addStatus" class="add_dia">Добавить статус</button>
  </div>
</template>

<script>
export default {
  name: "Status",
  components: {},
  props: {
    statuses: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      statusTypes: [
        "Активна",
        "Неактивна",
        "Заблокирована",
        "Утеряна",
        "Изготавливается",
      ],
      statuses_prop: this.statuses,
    };
  },
  methods: {
    selectionChange() {
      console.log(this.statuses);
    },
    addStatus() {
      this.statuses_prop.push("Неактивна");
    },
  },
};
</script>

<style></style>
