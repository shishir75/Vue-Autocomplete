<template>
  <div class="about">
    <div style="background-color: red;position: absolute; height: 300px" @click="model = false"></div>


    <h1>This is an about page</h1>

    <input type="text" v-model="state" autocomplete="off" @focus="model = true" >

    <div v-if="filteredStates && model" style="width: 300px; margin: auto">
      <ul style="list-style-type: none;">
        <li v-for="filteredState in filteredStates" v-bind:key="filteredState" @click="setState(filteredState)" style="cursor: pointer; background-color: gray; padding: 5px 10px 5px; margin-top: 2px; color: white">{{ filteredState }}</li>
      </ul>
    </div>

  </div>
</template>


<script>
  export default {
    data: function () {
      return {
        state: '',
        model: false,
        states: [
                'Dhaka', 'Rangpur', 'Rajshahi', 'Barishal', 'Chattragam'
        ],
        filteredStates: '',
      }
    },

    mounted() {
      this.filterStates();
    },

    methods: {
      filterStates() {
        if (this.state.length == 0) {
          this.filteredStates = this.states;
        }

        this.filteredStates = this.states.filter(state => {
          return state.toLowerCase().startsWith(this.state.toLowerCase());
        });
      },
      setState(state) {
        this.state = state;
        this.model = false;
      }
    },

    watch: {
      state() {
        this.filterStates();
      }
    },
  }
</script>
