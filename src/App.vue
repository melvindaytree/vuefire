<template>
  <div id="app">
    <h1><u>Melvin's Item Transaction Page</u></h1>
    <br />
<div class="">
      <div class="">
        <h3 class="panel-title">Add Items</h3>
      </div>
      
         <form id="form" class="" v-on:submit.prevent="addItem">
        <div class="row">
          <div class="col-md-4">
            <label for="status">Status:</label>
            <input type="text" id="status" class="form-control" v-model="newItem.status">
          </div>
          <div class="col-md-4">
            <label for="file_name">File Name:</label>
            <input type="text" id="file_name" class="form-control" v-model="newItem.file_name">
          </div>
          <div class="col-md-4">
            <label for="received_date">Received Date:</label>
            <input type="text" id="received_date" class="form-control" v-model="newItem.received_date">
          </div>
        </div>
        <div class="row">
          <div class="col-md-4">
            <label for="requested_user">Requested User:</label>
            <input type="text" id="requested_user" class="form-control" v-model="newItem.requested_user">
          </div>
          <div class="col-md-4">
            <label for="transactions">Transactions:</label>
            <input type="text" id="transactions" class="form-control" v-model="newItem.transactions">
          </div>
        </div>

          <input type="submit" class="btn btn-primary margin-submit" value="Add Item">
        </form>
      </div>
    <br />
<div>

  <h3>Item Database</h3>
    <div class="my-1 row">
      <div class="col-md-6">
        <b-form-group horizontal label="Rows per page" :label-cols="6">
          <b-form-select :options="pageOptions" v-model="perPage" />
        </b-form-group>
      </div>
      <div class="col-md-6">
        <b-form-group horizontal label="Filter" :label-cols="3">
          <b-input-group>
            <b-form-input v-model="filter" placeholder="Type to Search" />
            <b-input-group-button>
              <b-btn @click="filter = ''">Clear</b-btn>
            </b-input-group-button>
          </b-input-group>
        </b-form-group>
      </div>
    </div>

   <div class="row my-1">
      <div class="col-sm-8">
        <b-pagination :total-rows="totalRows" :per-page="perPage" v-model="currentPage" />
      </div>
      <div class="col-sm-4 text-md-right">
        <b-button :disabled="!sortBy" @click="sortBy = null">Clear Sort</b-button>
      </div>
    </div>

<b-table striped hover 
          :items="items" 
          :fields="fields" 
          :filter="filter" 
          :sort-by.sync="sortBy"
          :sort-desc.sync="sortDesc"
          :per-page="perPage"
          :current-page="currentPage"
          @filtered="onFiltered">
        </b-table>

</b-container>
</div>
</div>
</template>

<script>
 import Hello from './components/Hello'

  // This line is new!
  import Firebase from 'firebase'

  /*
   * The config was copied and pasted straight from the Firebase Dashboard.
   * Simply click "Add Firebase to Your Web App" to access yours.
   */

  let config = {
    apiKey: 'AIzaSyCM9WGU4G-CjkZZmBGUlM8F0ZVG6MPI0KI',
    authDomain: 'vuejs-f6a57.firebaseapp.com',
    databaseURL: 'https://vuejs-f6a57.firebaseio.com',
    projectId: 'vuejs-f6a57',
    storageBucket: 'vuejs-f6a57.appspot.com',
    messagingSenderId: '221000683687'
  }

  // Here we are initializing the Firebase connection.
  let app = Firebase.initializeApp(config)
  let db = app.database()

  // Accessing the greetings reference; .ref() takes a URL as its parameter.
  let vueRef = db.ref('items')

  export default {
    name: 'app',

    firebase: {
      items: vueRef
    },

    components: {
      Hello
    },

    data () {
    return {

       fields: [
        {
          key: 'status',
          sortable: true
        },
        {
          key: 'file_name',
          sortable: true
        },
        {
          key: 'received_date',
          sortable: true
        },
        {
          key: 'requested_user',
          sortable: true
        },
        {
          key: 'transactions',
          sortable: true
        }
      ],


      newItem: {
          file_name: '',
          is_active: '',
          received_date: '',
          requested_user: '',
          status: '',
          transactions: ''
      },

      

      currentPage: 1,
      perPage: 5,
      totalRows: 5,
      pageOptions: [{text: 5, value: 5}, {text: 10, value: 10}, {text: 15, value: 15}],
      sortBy: null,
      sortDesc: false,
      filter:null 
    }
  },

  methods: {
      addItem: function () {
        vueRef.push(this.newItem);
        this.newItem.status = '';
        this.newItem.file_name = '';
        this.newItem.received_date = '';
        this.newItem.requested_user = '';
        this.newItem.transactions = '';
      },
    },
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.margin-submit {
  margin-top:15px;
  margin-bottom:15px;
}

</style>
