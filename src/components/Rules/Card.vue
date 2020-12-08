<template>
  <div class="pad">
    <ul>
      <li v-for="(cardType, i) of cardTypes" :key="cardType">
        <br />
        <span v-if="i > 0" class="or"> или</span> Тип {{ i + 1 }}
        <select
          @change="selectionChange"
          v-model="cardTypes_prop[i]"
          class="sel"
        >
          <option v-for="j of cards" :key="j">{{ j }}</option>
        </select>
        <br />
      </li>
      <br />
    </ul>
  </div>
  <button @click="addType"  class="add_dia" >Добавить тип</button>
</template>

<script>
export default {
  name: "Card",
  props: {
    cardTypes: {
      type: Array,
      required: true,
    },
  },
  components: {},
  data() {
    return {
      cards: ["Silver", "Gold", "Platinum"],
      cardTypes_prop: this.cardTypes,
    };
  },
  methods: {
    addType() {
      this.cardTypes_prop.push("Silver");
    },
    selectionChange() {
      console.log(this.cardTypes);
    },
  },
};
</script>

<style>
.pad {
  padding-top: 20px;
}

.or {
  width: 2%;
  height: 20px;
  background-color: rgb(233, 123, 34);

  border-radius: 20% 20% 20% 20%;
}
.sel {
  position: absolute;
  left: 200px;
  width: 100px;
}
.add_dia {
  border: 2px solid #00e900; /* Green */
  display: inline-block;
  vertical-align: middle;
  border-radius: 10% 10% 10% 10%;
  font-family: Arial, Helvetica, sans-serif;
  background-color: #fff;
  color: #95a595;
  width: 15%;
}
</style>
