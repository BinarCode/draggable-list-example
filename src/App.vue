<template>
    <div id="app" class="min-h-screen w-screen bg-gray-200 flex items-center justify-center">
        <draggable tag="ul"
                   class="w-full max-w-md"
                   ghost-class="moving-card"
                   :list="users"
                   :animation="200">
            <user-card v-for="user in users"
                       :user="user"
                       :key="user.id"
                       @on-edit="onEdit"
                       @on-delete="onDelete">
            </user-card>
        </draggable>
    </div>
</template>

<script>
  import Draggable from 'vuedraggable'
  import UserCard from "./components/UserCard";
  export default {
    name: "App",
    components: {
      Draggable,
      UserCard,
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
