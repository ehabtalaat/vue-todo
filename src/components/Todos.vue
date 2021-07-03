 <template>
  <div>
    <div :key="todo.id" v-for="todo in todos">
      <Item :todo="todo" @dele-todo="$emit('dele-todo',todo.id)" />
    </div>
  </div>
</template>

<script>
import Item from './Item';

export default {
  name: "Todos",
  components: {
    Item
  },
  props: ["todos"] 
  // i pass pros (todos)  from home and put it in props an us it in v-for and pass todo to item and use it their

}
</script>

<style scoped>

</style>
