<template>
    <div>
      <h1>The sidebar is {{ collapsed ? 'closed' : 'open' }}</h1>
      <button
            :class="['toggle-button', { 'open-button': !collapsed }]"
            @click="toggleSidebar"
    >
        <span v-if="collapsed">Open Sidebar</span>
        <span v-else>Close Sidebar</span>
    </button>
    </div>
  </template>

  <script>
  import { collapsed, toggleSidebar } from '@/components/sidebar/state'

  export default {
    setup() {
      return { collapsed, toggleSidebar }
    },
  }
  </script>

  <style scoped>
  .toggle-button {
    padding: 10px 20px;
    font-size: 16px;
    border: none;
    border-radius: 5px;
    background-color: #4caf50;
    color: white;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .toggle-button:hover {
    background-color: #45a249;
  }

  .toggle-button:focus {
    outline: none;
  }
  .open-button{
  background-color: #e74c3c; /* Red color when sidebar is closed */
}
  </style>
