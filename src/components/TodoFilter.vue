<template>
  <div :class="$style.filter_container">
    <div class="length">
      <span>{{ todos.length }} items left</span>
    </div>
    <div :class="$style.filters">
      <ul>
        <li
          v-for="link in links"
          :key="link.id"
          :class="[activeId === link.id ? $style.active : null]"
          @click="selectLink(link.id)"
        >
          {{ link.title }}
        </li>
      </ul>
    </div>
    <div :class="$style.clear">
      <button :class="$style.btn">Clear Completed</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoFilter",
  props: {
    todos: Array,
  },
  data() {
    return {
      activeId: 1,
      links: [
        { id: 1, title: "All" },
        { id: 2, title: "Active" },
        { id: 3, title: "Completed" },
      ],
    };
  },
  methods: {
    selectLink(id) {
      this.activeId = id;
    },
  },
};
</script>

<style module lang="scss">
.filter_container {
  background-color: #25273d;
  width: 100%;
  color: #5b5e7e;
  font-size: 1.4rem;

  display: flex;
  padding: 1.6rem 2rem;
  align-items: center;
  justify-content: space-between;

  .filters {
    ul {
      display: flex;
    }
    li {
      list-style: none;
      cursor: pointer;

      &:not(:last-child) {
        margin-right: 1rem;
      }

      &:hover:not(.active) {
        color: #fff;
      }
    }

    .active {
      color: #3a7cfd;
    }
  }

  .clear {
    .btn {
      background-color: transparent;
      outline: none;
      border: none;
      color: inherit;
      cursor: pointer;

      &:hover {
        color: #fff;
      }
    }
  }
}
</style>
