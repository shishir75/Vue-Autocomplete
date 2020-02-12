<template>
  <div class="about">
    <h1>This is an about page</h1>

    <input type="text" v-model="state" autocomplete="off" @input="filterStates">

  </div>
</template>


<script>
  export default {
    data: function () {
      return {
        state: '',
        states: [
                'Dhaka', 'Rangpur', 'Rajshahi', 'Barishal', 'Chattragam'
        ],
        filteredStates: '',
      }
    },

    methods: {
      filterStates() {
        this.filteredStates = this.states.filter(state => {
          return state.toLowerCase().startsWith(this.state.toLowerCase());
        });
      }
    }
  }
</script>
