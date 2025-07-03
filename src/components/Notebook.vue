<script setup>
import { ref } from 'vue'

const notes = ref([
  {
    id: 1,
    title: 'Physics: Newton\'s Laws',
    content: 'First law: An object at rest stays at rest...',
    date: '2024-01-15',
    subject: 'Physics',
    color: 'badge-primary'
  },
  {
    id: 2,
    title: 'Math: Quadratic Equations',
    content: 'ax² + bx + c = 0, discriminant = b² - 4ac',
    date: '2024-01-14',
    subject: 'Mathematics',
    color: 'badge-secondary'
  },
  {
    id: 3,
    title: 'History: World War II',
    content: 'Key dates and events from 1939-1945',
    date: '2024-01-13',
    subject: 'History',
    color: 'badge-accent'
  }
])

const showNewNote = ref(false)
const newNote = ref({
  title: '',
  content: '',
  subject: ''
})

const addNote = () => {
  if (newNote.value.title && newNote.value.content) {
    notes.value.unshift({
      id: notes.value.length + 1,
      title: newNote.value.title,
      content: newNote.value.content,
      date: new Date().toISOString().split('T')[0],
      subject: newNote.value.subject || 'General',
      color: 'badge-primary'
    })
    newNote.value = { title: '', content: '', subject: '' }
    showNewNote.value = false
  }
}
</script>

<template>
  <div class="p-4 max-w-2xl mx-auto">
    <div class="flex justify-between items-center mb-4">
      <h2 class="text-2xl font-bold">My Notebook</h2>
      <button @click="showNewNote = true" class="btn btn-primary btn-sm">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
        </svg>
        New Note
      </button>
    </div>
    
    <!-- New Note Modal -->
    <div v-if="showNewNote" class="modal modal-open">
      <div class="modal-box">
        <h3 class="font-bold text-lg mb-4">Create New Note</h3>
        <form @submit.prevent="addNote" class="space-y-4">
          <div class="form-control">
            <label class="label">
              <span class="label-text">Title</span>
            </label>
            <input 
              v-model="newNote.title"
              type="text" 
              placeholder="Note title" 
              class="input input-bordered w-full"
              required
            />
          </div>
          <div class="form-control">
            <label class="label">
              <span class="label-text">Subject</span>
            </label>
            <input 
              v-model="newNote.subject"
              type="text" 
              placeholder="e.g., Math, Physics" 
              class="input input-bordered w-full"
            />
          </div>
          <div class="form-control">
            <label class="label">
              <span class="label-text">Content</span>
            </label>
            <textarea 
              v-model="newNote.content"
              class="textarea textarea-bordered h-32" 
              placeholder="Write your note here..."
              required
            ></textarea>
          </div>
          <div class="modal-action">
            <button type="button" @click="showNewNote = false" class="btn">Cancel</button>
            <button type="submit" class="btn btn-primary">Save Note</button>
          </div>
        </form>
      </div>
    </div>
    
    <!-- Notes Grid -->
    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <div 
        v-for="note in notes" 
        :key="note.id"
        class="card bg-base-200 shadow-md hover:shadow-lg transition-shadow cursor-pointer"
      >
        <div class="card-body">
          <div class="flex justify-between items-start mb-2">
            <h3 class="card-title text-lg">{{ note.title }}</h3>
            <div :class="['badge', note.color]">{{ note.subject }}</div>
          </div>
          <p class="text-base-content/70 line-clamp-3">{{ note.content }}</p>
          <div class="card-actions justify-between items-center mt-4">
            <span class="text-sm text-base-content/50">{{ note.date }}</span>
            <div class="space-x-2">
              <button class="btn btn-ghost btn-xs">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z" />
                </svg>
              </button>
              <button class="btn btn-ghost btn-xs">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>