<template>
  <div id="app">
    <Tabs>
      <Tab name="Параметры">
        <Params />
      </Tab>
      <Tab name="Вопросы">
        <Questions />
      </Tab>
      <Tab name="Логика">
        <Logic />
      </Tab>
      <Tab name="Условия">
        <Rules />
      </Tab>
      <Tab name="Респонденты" selected="true">
        <Poll />
      </Tab>
    </Tabs>
  </div>
</template>

<script>
import Tab from "@/views/Tab";
import Poll from "@/components/Poll";
import Questions from "@/components/Questions";
import Params from "@/components/Params";
import Rules from "@/components/Rules";
import Logic from "@/components/Logic";
import Tabs from "@/views/Tabs";

export default {
  components: {
    Poll,
    Questions,
    Tab,
    Params,
    Logic,
    Rules,
    Tabs,
  },
  name:'App'
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  border: 1px solid gray
}
</style>
