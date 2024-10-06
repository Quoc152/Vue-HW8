<script setup>
import { computed } from 'vue'
import { User, Briefcase, CalendarDays } from 'lucide-vue-next'

const props = defineProps({
  avatar: {
    type: String,
    default: '/placeholder.svg?height=100&width=100'
  },
  fullName: {
    type: String,
    default: 'John Doe'
  },
  job: {
    type: String,
    default: 'Software Engineer'
  },
  age: {
    type: Number,
    default: 30
  },
  joinedDate: {
    type: String,
    default: '2023-01-01'
  },
  gradientBorder: {
    type: String,
    default: 'linear-gradient(to right, #ff00cc, #3333ff)'
  }
})

const formattedJoinedDate = computed(() => {
  return new Date(props.joinedDate).toLocaleDateString()
})
</script>

<template>
  <div class="w-full max-w-sm mx-auto">
    <div class="relative p-1 rounded-xl overflow-hidden" :style="{ background: gradientBorder }">
      <div class="bg-white dark:bg-gray-800 p-6 rounded-lg space-y-4">
        <div class="flex items-center space-x-4">
          <img
            :src="avatar"
            :alt="`${fullName}'s avatar`"
            class="w-20 h-20 rounded-full object-cover"
          />
          <div>
            <h2 class="text-2xl font-bold text-gray-800 dark:text-white">{{ fullName }}</h2>
            <p class="text-gray-600 dark:text-gray-300">{{ job }}</p>
          </div>
        </div>
        <div class="space-y-2">
          <div class="flex items-center text-gray-700 dark:text-gray-200">
            <User class="w-5 h-5 mr-2" />
            <span>{{ age }} years old</span>
          </div>
          <div class="flex items-center text-gray-700 dark:text-gray-200">
            <Briefcase class="w-5 h-5 mr-2" />
            <span>{{ job }}</span>
          </div>
          <div class="flex items-center text-gray-700 dark:text-gray-200">
            <CalendarDays class="w-5 h-5 mr-2" />
            <span>Joined on {{ formattedJoinedDate }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
