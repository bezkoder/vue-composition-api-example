<template>
  <div>
    <p>{{ vTitle }}</p>

    <div class="my-3 text-primary">
      <p>{{ append }}</p>
    </div>
    
    <div class="form-group d-flex">
      <input v-model="todo" type="text" class="form-control" />
      <button class="btn btn-primary" @click="add">Add</button>
    </div>
    <p>[TodoLength: {{ todoLength }}, Items quantity: {{ itemsQuantity }}]</p>

    <div class="list-group">
      <div
        class="list-group-item d-flex justify-content-between"
        v-for="(item,index) in items"
        :key="index"
      >
        <span>{{ item }}</span>
        <button class="close" @click="remove(index)">
          <span>&times;</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    initInput: String
  },
  computed: {
    vTitle() {
      return '-' + this.title + '-';
    },
    itemsQuantity() {
      return this.items.length;
    }
  },
  data() {
    return {
      todo: this.initInput,
      todoLength: 0,
      items: ['This', 'is'],
      append: ''
    };
  },
  watch: {
    todo: {
      handler: function(value, oldValue) {
        this.todoLength = value.length;
      },
      immediate: true
    },
    items: {
      handler: function(value, oldValue) {
        this.append = '';
        value.forEach(item => {
          this.append += item + ' ';
        });
      },
      immediate: true
    }
  },
  methods: {
    add() {
      if (this.todo) {
        this.items.push(this.todo);
        this.todo = '';
      }
    },

    remove(index) {
      this.items.splice(index, 1);
    }
  },
  beforeMount() {
    console.log('V2 beforeMount!')
  },
  mounted() {
    console.log('V2 mounted!')
  }
};
</script>
