<!-- Please remove this file from your project -->
<template>
  <div class="">
    <form>
  <div class="form-group">
    <label for="exampleInputEmail1">Email address</label>
    <input v-model="email" type="email"  class="form-control" aria-describedby="emailHelp">
    <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
  </div>
  <div class="form-group">
    <label for="exampleInputPassword1">Password</label>
    <input v-model="password" type="password" class="form-control" >
  </div>
  
  <button type="submit" @click="submitdata()">Submit</button>
</form>

<!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
  Launch demo modal
</button>

<!-- Modal -->
<div id="exampleModal" class="modal fade"  tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5  id="exampleModalLabel" class="modal-title">Modal title</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <input v-model="test" type="text" class="form-control">
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      email:'',
      password:'',
      test:''
    }
  },

mounted() {
  this.socket = this.$nuxtSocket({
    // nuxt-socket-io opts: 
    name: 'work', // Use socket "home"
    channel: '/', // connect to '/index'

    // socket.io-client opts:
    reconnection: false
  })
 
},
methods: {
  submitdata(){
   this.socket.emit('testna',{email:this.email,password:this.password})
  },
  getMessage() {
    this.socket.emit('testna',{data:"test na"})
  } 
}
}
</script>
