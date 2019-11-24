<template>
    <div id="app" class="min-h-screen w-screen bg-gray-200 flex items-center justify-center">
        <draggable tag="ul"
                   class="w-full max-w-md"
                   ghost-class="moving-card"
                   :list="users"
                   :animation="200">
            <li v-for="user in users"
                :key="user.id"
                class="p-4 mb-3 flex justify-between items-center bg-white shadow rounded-lg cursor-move">
                <div class="flex items-center">
                    <img class="w-10 h-10 rounded-full" :src="user.avatar" :alt="user.name">
                    <p class="ml-2 text-gray-700 font-semibold font-sans tracking-wide">{{user.name}}</p>
                </div>
                <div class="flex">
                    <button aria-label="Edit user"
                            class="p-1 focus:outline-none focus:shadow-outline text-teal-500 hover:text-teal-600"
                            @click="onEdit(user)">
                        <EditIcon/>
                    </button>
                    <button aria-label="Delete user"
                            class="p-1 focus:outline-none focus:shadow-outline text-red-500 hover:text-red-600"
                            @click="onDelete(user)">
                        <Trash2Icon/>
                    </button>
                </div>
            </li>
        </draggable>
    </div>
</template>

<script>
  import { EditIcon, Trash2Icon } from "vue-feather-icons";
  import Draggable from 'vuedraggable'

  export default {
    name: "App",
    components: {
      Draggable,
      EditIcon,
      Trash2Icon
    },
    data() {
      return {
        users: [
          {
            id: 1,
            name: "Adrian Schubert",
            avatar: "https://pickaface.net/gallery/avatar/unr_sample_161118_2054_ynlrg.png"
          },
          {
            id: 2,
            name: "Violet Gates",
            avatar: "https://pickaface.net/gallery/avatar/freud51c8b3f65e7dc.png"
          },
          {
            id: 3,
            name: "Steve Jobs",
            avatar: "https://pickaface.net/gallery/avatar/Opi51c74d0125fd4.png"
          },
          {
            id: 4,
            name: "Yassine Smith",
            avatar: "https://pickaface.net/gallery/avatar/unr_yassine_191124_2012_3gngr.png"
          },
          {
            id: 5,
            name: "Senior Saez",
            avatar: "https://pickaface.net/gallery/avatar/elmedinilla541c03412955c.png"
          }
        ]
      }
    },
    methods: {
      onEdit(user) {
        alert(`Editing ${user.name}`);
      },
      onDelete(user) {
        alert(`Deleting ${user.name}`);
      }
    }
  }
</script>

<style lang="scss">
    .moving-card {
        @apply opacity-50 bg-gray-100 border border-blue-500;
    }
</style>
