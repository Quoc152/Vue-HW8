<script setup>
import { ref, onMounted } from 'vue'
import UserProfileCard from './components/UserProfileCard.vue'

const users = ref([
  {
    avatar: '',
    fullName: 'Le Bao Quoc',
    job: 'Software Engineer',
    age: 28,
    joinedDate: '2022-03-15'
  },
  {
    avatar: '',
    fullName: 'Nguyen Van A',
    job: 'UX Designer',
    age: 32,
    joinedDate: '2021-11-01'
  },
  {
    avatar: '',
    fullName: 'Nguyen Van B',
    job: 'Product Manager',
    age: 35,
    joinedDate: '2020-07-22'
  },
  {
    avatar: '',
    fullName: 'Nguyen Van C',
    job: 'Data Scientist',
    age: 29,
    joinedDate: '2023-01-10'
  },
  {
    avatar: '',
    fullName: 'Nguyen Van D',
    job: 'Marketing Specialist',
    age: 31,
    joinedDate: '2022-09-05'
  }
])

const gradients = ref([])

const generateRandomGradient = () => {
  const color1 = Math.floor(Math.random()*16777215).toString(16)
  const color2 = Math.floor(Math.random()*16777215).toString(16)
  return `linear-gradient(to right, #${color1}, #${color2})`
}

onMounted(() => {
  gradients.value = users.value.map(() => generateRandomGradient())
})
</script>

<template>
  <div class="container mx-auto p-4">
    <h1 class="text-3xl font-bold mb-6 text-center text-gray-800 dark:text-white">User Profiles</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <UserProfileCard
        v-for="(user, index) in users"
        :key="index"
        :avatar="user.avatar"
        :fullName="user.fullName"
        :job="user.job"
        :age="user.age"
        :joinedDate="user.joinedDate"
        :gradientBorder="gradients[index]"
      />
    </div>
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
