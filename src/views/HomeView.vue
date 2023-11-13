<template>
  <div class="home">
    <h1>Mordes</h1>
    <!-- <p ref="p">{{ name }}({{age  }})</p>
    <button @click="handleClick">Clickety</button>
    <input type="text " v-model="name"> -->
    <!-- <button @click="age++">up age</button> -->

    <!-- <div>
      <p>{{ninjaOne.name  }}({{ ninjaOne.age }})</p>
      <button @click="updateNinja">Okay</button>
    </div>
    <div>
      <h2>Reactive</h2>
      <p>{{spiderman.name  }}({{ spiderman.age }})</p>
      <button @click="updateSpider">Okay</button>
    </div>
  </div> -->
  <!-- Compostion API part 1 -->
  <!-- <div>
    <input  type="text" v-model="search">
    <p>search term - {{ search }}</p>

    <div v-for="name in matchingNames" :key="name">
      <p>{{ name }}</p>
    </div>
  </div>
  <button @click="stopEffect">Staaaahhp</button> -->
  <div v-if="error">{{ error }}</div>
  <div v-if="posts.length">
    <PostList v-if="showPosts" :posts="posts"/>
  </div>
  <div v-else>Loading...</div>
  <button  @click="showPosts=!showPosts">toggle Posts</button>
  <button @click="posts.pop()">Delete a post</button>

</div>
</template>

<script>
import PostList from '../components/PostList.vue'
import { ref,reactive, computed, watch, watchEffect } from 'vue'
import getPosts from '../composables/getPosts'
// @ is an alias to /src

export default {
  name: 'HomeView',
  components:{PostList},
 setup(){
//   const spiderman=reactive({name:'Miles',age:16})
//   const ninjaOne=ref({name:'mario',age:30})

//   const updateNinja=()=>{
//     ninjaOne.value.age=40
//   }
//   const updateSpider=()=>{
//     spiderman.age=22
//   }

//   return {ninjaOne, updateNinja,spiderman,updateSpider}

///////////////////////////////////////////////////////
// Composition API
// const names=ref(['peter','miles','mary','jane','may','ben','richard'])
// const search=ref('')

// const stopWatch=watch(search,()=>{
//   console.log('im watching you')
// })
// const stopEffect=watchEffect(()=>{
//   console.log('Effectively watching you',search.value)
// })
// const matchingNames=computed(()=>{
//   return names.value.filter((name)=>name.includes(search.value))
// })
// return {names,search,matchingNames,stopEffect,stopWatch}
//  },

// ////////////////////////////
// Composition API Part 2
const showPosts=ref(true)
  const { posts ,error,load}=getPosts()
  load()

  return {posts,showPosts ,error}
}


}
</script>
<style >


</style>
