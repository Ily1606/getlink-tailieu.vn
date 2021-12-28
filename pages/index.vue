<template>
<div class="md:mt-20 mt-4 container mx-auto">
    <div class="max-w-7xl">
      <div class="text-center font-bold text-green-500 text-7xl">Get link tailieu.vn</div>
      <div>
        <form @submit="submit">
          <div class="my-2">
            <label for="link" class="my-3">
              Link tailieu.vn
            </label>
            <input type="text" v-model="link" id="link" placeholder="Paste link here..." class="border focus:outline-green-400 rounded-md w-full p-2" />
          </div>
          <div class="my-2">
            <button v-if="!loading" class="bg-green-500 rounded-md p-2 text-white">Get link</button>
            <button v-else class="bg-green-500 rounded-md p-2 text-white disabled:bg-green-300" disabled>Getting...</button>
          </div>
          <div class="my-4 border border-green-500 rounded-md p-4" v-if="result">
            Paste to your browser: {{result}}
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      link: '',
      loading: false,
      result: null
    }
  },
  layout: "default",
  methods:{
    submit(e){
      e.preventDefault();
      if(this.link !== ''){
        this.loading = true;
        setTimeout(() =>{
          this.loading = false;
          const data = this.link.split('-')[this.link.split('-').length - 1]
          this.result = `https://tailieu.vn/document/downfiletlvnb3a?docid=${btoa(data.split('.html')[0])}`
        },3000);
      }
      else{
        alert("Please enter link!");
      }
    }
  }
}
</script>
