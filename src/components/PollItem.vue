<template>
  <a v-if="index > 0">И </a>
  <br />
  <div class="f">
    <br />
    <span :class="{'c1': (index%3===0),'c2':(index%3===1),'c3':(index%3===2)}">
      Условие
      <strong>{{ index + 1 }}</strong>
    </span>
    <span style="padding: 0px 20px;">&nbsp;</span>
    <select id="id_of_select" @change="onSelect" v-model="pollItem_prop.type">
      <option disabled value="">Выберите условие</option>
      <option value="Age">Возраст респондента</option>
      <option value="CardType" selected="true">Тип Карты Лояльности</option>
      <option value="Status" selected>Статус</option>
    </select>
    <span id="rules">
      <Age
        v-bind:ageRanges="pollItem_prop.data"
        v-if="pollItem_prop.type == 'Age'"
      />
      <Card
        v-bind:cardTypes="pollItem_prop.data"
        v-if="pollItem_prop.type == 'CardType'"
      />
      <Status
        v-bind:statuses="pollItem_prop.data"
        v-if="pollItem_prop.type == 'Status'"
      />
    </span>
    <div class="r">
      <button class="rm" v-on:click="$emit('remove-poll-item', pollItem.id)">
        Удалить условие
      </button>
    </div>
  </div>
</template>

<script>
import Age from "@/components/Rules/Age";
import Card from "@/components/Rules/Card";
import Status from "@/components/Rules/Status";

export default {
  props: {
    pollItem: {
      type: Object,
      required: true,
    },
    index: Number,
  },
  components: {
    Age,
    Card,
    Status,
  },

  data() {
    return {
      pollItem_prop: this.pollItem, // Здесь переназначаем пропс
    };
  },
  methods: {
    onSelect() {
      if (this.pollItem_prop.type === "Age") {
        this.pollItem_prop.data = [{ from: "15", to: "45" }];
      }
      if (this.pollItem_prop.type === "CardType") {
        this.pollItem_prop.data = ["Silver"];
      }
      if (this.pollItem_prop.type === "Status") {
        this.pollItem_prop.data = ["Неактивна"];
      }
    },
  },
};
</script>

<style scoped>
.rm {
  display: flex;
  justify-content: end;
  background: red;
  color: #fff;
  border-radius: 10% 10% 10% 10%;
  font-weight: bold;
}

input {
  margin-right: 1rem;
}
.f {
  border: 1px solid rgb(223, 222, 222);
  padding-bottom: 5%;
  padding: 1rem;
  text-align: left;
  position: relative;
  width: 1500px;
}
.r {
  display: block;
  justify-content: end;
  margin-left: 75%;
  position: relative;
}
.c1 {
  color: cyan;
}
.c2 {
  color: rgb(107, 120, 214);
}
.c3 {
  color: rgb(17, 175, 69);
}
a{
  width:2%;
  height: 20px;
  background-color: rgb(171, 233, 225);
  position: absolute;
  left:3.5%;
  border-radius: 20%
}
</style>
