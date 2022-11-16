<template>
  <div>
    <div v-scroll="handleScroll" class="box1">
      <h1>Bringing passion into your video</h1>
      <p>Phase 3 came about from a desire to do more for the Videography Industry.</p>
      <img src="https://images.unsplash.com/photo-1509873564860-e4b86950dd4f?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8bWFuJTIwaG9sZGluZyUyMGNhbWVyYXxlbnwwfHwwfHw%3D&w=1000&q=80">
    </div>
    
  </div>
</template>

<script>

import Vue from 'vue';
Vue.directive('scroll', {
  inserted: function (el, binding) {
    let f = function (evt) {
      if (binding.value(evt, el)) {
        window.removeEventListener('scroll', f)
      }
    }
    window.addEventListener('scroll', f)
  }
})

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      new_message: 'suck ma wiggly dick!',
      meessage: 'AWOOGA',
    }
  },
  methods: {

    handleScroll: function (evt, el) {
      //value of the elements distance from the center of the y value of the screen.
      let dist_to_center = (el.getBoundingClientRect().bottom - (el.offsetHeight / 2) - (window.innerHeight / 2));
      //lerp values should be between 0 and 1. 0 being the center of the window.
      //enter_lerp should always be less than or equal to the exit_lerp
      const enter_lerp = 0;
      const exit_lerp = 1;
      if (dist_to_center < ((window.innerHeight / 2) * enter_lerp)) {
        
        el.setAttribute(
          //attributes style changes when triggered are here    
          'style',
          'opacity: 1; transform: translate3d(0, 0, 0)'
        );
        console.log(this.$el.getElementsByTagName('h1')[0]);
        this.$el.getElementsByTagName('h1')[0].hidden=false;
      }
      else if (dist_to_center > (window.innerHeight / 2) * exit_lerp) {
        
        el.setAttribute(
          //attributes style changes when not triggered are here    
          'style',
          'opacity: 0; transform: translate3d(0, 20px, 0);'
        );
        
        setTimeout(() => {
          this.$el.getElementsByTagName('h1')[0].hidden=true
        }, 1500);

        
      }
    },

  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.box1 {
  opacity: 0;
  transition: 1.5s all cubic-bezier(0.39, 0.575, 0.565, 1);

  min-height: 100vh;
  h1 {
    color: #eaeaea;
    font-size: 6rem;
    font-variant-caps: all-petite-caps;
    width: 50%;
    text-align:left;
    position:absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    mix-blend-mode: difference;
    animation: appear 1.5s forwards;
    opacity: 0;
    animation-delay: 2.1s;


  }
  p {
    color: #c6c6c6;
    font-size: 2rem;
    width: 50%;
    text-align:right;
    position:absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  img {
    max-width: 50%;
    max-height: 50%;
    position:absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: -10;
  }
}

.box1 :nth-child(1) {
  top: 30%;
  left: 30%;

}

.box1 :nth-child(2) {
  top: 60%;
  left: 70%;

}

.box1 :nth-child(3) {
  top: 60%;
  left: 40%;
  
}

@keyframes appear {
  0% {
    opacity: 0;

  }
  100% {
    opacity: 1;
  }
}

</style>
