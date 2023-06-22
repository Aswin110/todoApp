<template>
  <div class="container">
    <h2 class="text-center mt-5">My Vue Todo App</h2> 
    <!--input-->
    <div class="d-flex">
      <input type="text" placeholder="enter task " class="form-control">
      <button class="btn btn-warning rounded-0">SUBMIT</button>
    </div>

    <!--task table-->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">task</th>
          <th scope="col">status</th>
          <th scope="col" class="text-centre">#</th>
          <th scope="col" class="text-centre">#</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>watch kayal</td>
          <td>Mark</td>
          <td>Otto</td>
          <td>@mdo</td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
  export default {
  name: 'HelloWorld',
    props: {
      msg: String
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
