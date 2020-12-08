<template>
  <div class="pad">
    <ul>
      <li v-for="(ageRange, i) of ageRanges" :key="ageRange">
        <br />
        <span v-if="i > 0" class="or"> или</span>
        Диапазон {{ i + 1 }}
        <span class="from"
          >от&nbsp;
          <input type="text" name="from" v-model="ageRanges_prop[i].from" />
        </span>
        <span class="to"
          >до&nbsp;
          <input type="text" name="to" v-model="ageRanges_prop[i].to" />
        </span>
      </li>
      <br />
    </ul>
    <button @click="addRange" class="add_dia">Добавить диапазон</button>
  </div>
  <br />
</template>

<script>
export default {
  name: "Age",
  props: {
    ageRanges: {
      type: Object,
      required: true,
    },
  },
  components: {},
  data() {
    return { ageRanges_prop: this.ageRanges };
  },
  methods: {
    addRange() {
      var newItem = { from: "", to: "" };
      this.ageRanges_prop.push(newItem);
      console.log("added range", this.ageRanges_prop);
    },
  },
};
</script>

<style>
input {
  max-width: 30px;
}
li {
  list-style-type: none;
}
.pad {
  padding-top: 10px;
}
.from {
  position: absolute;
  left: 200px;
}
.to {
  position: absolute;
  left: 270px;
}
.or {
  width: 2%;
  height: 20px;
  background-color: rgb(233, 123, 34);

  border-radius: 20% 20% 20% 20%;
}
.add_dia {
  border: 2px solid #00e900; /* Green */
  display: inline-block;
  vertical-align: middle;
  border-radius: 10% 10% 10% 10%;
  font-family: Arial, Helvetica, sans-serif;
  background-color: #fff;
  color: #00e900;
  width: 15%;
}
</style>
