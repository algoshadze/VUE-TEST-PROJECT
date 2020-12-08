<template>
  <div class='f'>
    <ul >
      <PollItem
        v-for="(pollItem, i) of pollItems"
        :key="pollItem"
        v-bind:pollItem="pollItem"
        v-bind:index="i"
        v-on:remove-poll-item="removePollItem"
        
      />
    </ul>
  </div>
  <div>
    <br />
    <button class="add_button" @click="addPollItem">
      <span class="plus">+<br /></span
      ><span class="add_rule"
        >Нажмите, чтобы добавить условие выборки.<br />
        Все условия связываются между собой логическим "И"</span
      >
    </button>
  </div>
  <br />
  <div class="bottom">
   <div class="test_padding">
  <button class="test" @click="testPoll">Протестировать опрос</button>
   </div>
  </div>
</template>

<script>
import PollItem from "./PollItem";
export default {
  methods: {
    removePollItem(id) {
      console.log(id);
      this.pollItems = this.pollItems.filter((t) => t.id !== id);
    },
    addPollItem() {
      console.log("adding...");
      var newItem = { id: this.pollItems.length, type: "", data: null };
      this.pollItems.push(newItem);
    },
    testPoll() {
      console.log(this.pollItems);
    },
  },
  components: {
    PollItem,
  },
  data() {
    return {
      pollItems: [],
    };
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
.add_button {
  background-color: white;
  color: black;
  border: 2px solid #82ee86; /* Green */
  border-radius: 5% 5%;
  width: 40%;
  cursor: pointer;
}
.plus {
  font-weight: 100;
  font-size: 70px;
  font-family: a;
  color: #82ee86;
}
.add_rule {
  font-weight: 100;
  display: inline-block;
  vertical-align: middle;
  line-height: 1.25;
  font-family: Arial, Helvetica, sans-serif;
  color: #4cb350;
}
.test {
  display: block;
  position: relative;
  font-weight: 100;
  border: 2px solid #97a6af; /* Green */
  font-family: a;
  color: #48834a;

}
.test_padding{
  padding: 30px;
}
.bottom{
  background-color: rgb(221, 226, 226);
}
.f {

  border: 0.5px solid rgb(223, 222, 222);

  position: relative;
}


</style>
