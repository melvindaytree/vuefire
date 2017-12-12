<template>
<div>
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

        <b-col sm="12">
        <b-table striped hover 
          :items="items" 
          :fields="fields" 
          :filter="filter" 
          :sort-by.sync="sortBy"
          :sort-desc.sync="sortDesc"
          :per-page="perPage"
          :current-page="currentPage"
          @filtered="onFiltered">
        </b-table></b-col>



</b-container>
</div>
</div>
</template>

<script>

export default {
  name: 'hello',
  data () {
    return {

       fields: [
        {
          key: 'type',
          sortable: true
        },
        {
          key: 'date',
          sortable: true
        },
        {
          key: 'facility',
          label: 'Facility',
          sortable: true
        },
        {
          key: 'id',
          label: 'Id',
          sortable: true
        },
        {
          key: 'description',
          label: 'Description',
          sortable: false
        }
      ],
      items: [
        { isActive: true, type: 'Rollover', 
        date: '2017-10-19 10:30 AM', facility: 'Station Casinos TF', 
        id: '020D0AB277A6E', description: 'BLALBLBLALBLABLA' },
        { isActive: true, type: 'Standard', 
        date: '2017-05-20 10:30 AM', facility: 'Melvins Castle', 
        id: '140H0KR883D1E', description: 'This is just a test' },
        { isActive: true, type: 'Normal', 
        date: '2018-05-20 10:30 AM', facility: 'Boo Burg', 
        id: '931H0KR883D1E', description: 'Not a test' },
        { isActive: true, type: 'Normal', 
        date: '2018-05-20 10:30 AM', facility: 'Boo Burg', 
        id: '931H0KR883D1E', description: 'Not a test' },
        { isActive: true, type: 'Normal', 
        date: '2018-05-20 10:30 AM', facility: 'Boo Burg', 
        id: '931H0KR883D1E', description: 'Not a test' },
        { isActive: true, type: 'Normal', 
        date: '2018-05-20 10:30 AM', facility: 'Boo Burg', 
        id: '931H0KR883D1E', description: 'Not a test' },
        { isActive: true, type: 'Normal', 
        date: '2018-05-20 10:30 AM', facility: 'Boo Burg', 
        id: '931H0KR883D1E', description: 'Not a test' }
      ],
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
    onFiltered (filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length
      this.currentPage = 1
    }
  }
}
</script>