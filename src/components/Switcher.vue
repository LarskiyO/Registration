<template>
  <div class="accept-rules__switcher-wrap">
    <input type="checkbox" id="toggle" class="switcher" @click="setIsPublic" v-model="public"/>
    <label for="toggle" class="switcher-wrap"></label>
  </div>
</template>
<script>
  export default {
    name: 'Switcher',
    emits: ['public-updated'],
    methods: {
      setIsPublic() {
        this.public = !this.public;
        this.$emit('public-updated', this.public);
      }
    },
    data(){
      return {
        public: false
      }
    }
  };
</script>

<style>
  .switcher[type="checkbox"] {
    display: none;
  }
  
  .accept-rules__switcher-wrap {
    margin: 20px 0 0 27px;
  }
  
  .switcher-wrap {
    display: inline-block;
    width: 40px;
    height: 20px;
    background-color: white;
    border: 1px solid rgb(209, 209, 209);
    border-radius: 10px;
    position: relative;
    cursor: pointer;
    transition: background-color 0.2s ease;
  }
  
  .switcher-wrap:before {
    content: "";
    border: 1px solid rgb(209, 209, 209);
    position: absolute;
    width: 18px;
    height: 18px;
    border-radius: 50%;
    background-color: white;
    top: 0px;
    left: 0px;
    transition: transform 0.2s ease;
  }
  
  .switcher[type="checkbox"]:checked + .switcher-wrap {
    background-color: #3586FF;
  }
  
  .switcher[type="checkbox"]:checked + .switcher-wrap:before {
    transform: translateX(21px);
  }
  
  
  
  </style>
  