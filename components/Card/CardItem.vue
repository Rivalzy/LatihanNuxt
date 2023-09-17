<!-- eslint-disable vue/require-valid-default-prop -->
<!-- eslint-disable vue/no-mutating-props -->
<!-- eslint-disable vue/require-default-prop -->
<template>
  <div
    :class="[
      'item-task d-flex align-items-start border-bottom pt-3 pb-4',
      isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
    ]"
  >
    <input
      id="task"
      v-model="task.isDone"
      type="checkbox"
      name="status"
      class="me-2 mt-2"
      :checked="task.isDone"
    />
    <div
      :class="[
        'd-flex flex-column',
        task.isDone ? 'text-decoration-line-through fst-italic' : '',
      ]"
    >
      <div class="title-task mb-1">{{ task.title }}</div>
      <div class="description-task small text-muted">
        {{ task.description }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      // eslint-disable-next-line vue/require-valid-default-prop
      default: 'Untitled',
    },
    isGrid: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
}
</script>
