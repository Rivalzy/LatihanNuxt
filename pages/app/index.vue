<template>
  <div class="py-4">
    <div class="container">
      <div
        class="title border-bottom d-flex align-items-center justify-content-between py-2"
      >
        <h5>Task</h5>
        <div class="d-flex align-items-center">
          <button
            class="btn btn-outline-primary py-1 px-3 me-4"
            @click="shuffle"
          >
            Shuffle!
          </button>

          <input
            v-model="searchQuery"
            type="text"
            class="form-control"
            placeholder="Search"
          />

          <div class="d-flex align-items-center justify-content-end w-100">
            <span class="me-2">View As</span>
            <button
              class="btn btn-outline-secondary py-1 px-3"
              @click="isGrid = !isGrid"
            >
              {{ isGrid ? 'Grid' : 'List' }}
            </button>
          </div>
        </div>
      </div>

      <transition-group name="tasks" tag="div" class="list-task row">
        <CardItem
          v-for="(task,i) in resultQuery"
          :key="i"
          :task="task"
          :isGrid="isGrid"
        />
      </transition-group>

      <div v-if="searchQuery && resultQuery.length === 0" class="no-results">
        <h1>Pencarian tidak ditemukan.</h1>
      </div>

      <div class="action py-2">
        <a
          v-if="!isCreating"
          href="#"
          class="add-button"
          @click="isCreating = !isCreating"
          >Add Task</a
        >
        <!-- Form and Event Handler -->
        <form v-else v-on:submit.prevent="handleSubmit">
          <div class="add-card">
            <div class="card mb-2">
              <div class="card-body d-flex flex-column p-0">
                <input
                  v-model="newTask.title"
                  class="form-control border-0 mb-2"
                  placeholder="Title"
                  type="text"
                />
                <textarea
                  v-model="newTask.description"
                  class="form-control border-0 small"
                  placeholder="Description"
                  rows="3"
                ></textarea>
              </div>
            </div>
            <div class="button-wrapper d-flex">
              <button class="btn btn-primary me-2">Submit</button>
              <button
                class="btn btn-outline-secondary"
                @click="isCreating = !isCreating"
              >
                Cancel
              </button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import CardItem from '@/components/Card/CardItem.vue'

export default {
  components: {
    CardItem,
  },
  layout(context) {
    return 'custom'
  },
  data() {
    return {
      // Variabel penampung teks pencarian
      searchQuery: '',

      // Status saat menambahkan task
      isCreating: false,

      // Tipe layout daftar task
      isGrid: false,

      // daftar task
      tasks: [
        {
          title: 'Task 1',
          description: 'ini deskripsi',
          isDone: 'false',
        },
        {
          title: 'Tugas 2',
          description: 'ini deskripsi 2',
          isDone: false,
        },
        {
          title: 'Kerja 3',
          description: ' ini deskripsi 3',
          isDone: false,
        },
      ],
      newTask: {
        title: '',
        description: '',
        isDone: false,
      },
    }
  },

  computed: {
    resultQuery() {
      if (this.searchQuery) {
        return this.tasks.filter((item) => {
          return this.searchQuery
            .toLowerCase()
            .split(' ')
            .every((v) => item.title.toLowerCase().includes(v))
        })
      } else {
        console.log(this.tasks)
        return this.tasks
      }
    },
  },

  methods: {
    handleSubmit() {
      if (this.newTask.title.trim() !== '') {
        this.tasks.push(this.newTask)

        this.newTask = {
          title: '',
          description: '',
          isDone: false,
        }
        this.isCreating = false
      }
    },
    shuffle() {
      // eslint-disable-next-line no-undef
      this.tasks = _.shuffle(this.tasks)
    },
  },
}
</script>
<style>
#app .tasks-move {
  transition: 0.4s;
}

.no-results {
  text-align: center;
  font-size: 18px;
  margin-top: 20px;
  color: gray;
}
</style>
