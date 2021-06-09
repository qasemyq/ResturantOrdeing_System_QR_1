<template>
   <div>
      <div class="">
          <!-- Nav S -->
          <div class="navTop">
            <b-navbar type="dark" variant="dark">
                <b-navbar-nav>
                    <b-navbar-brand class="p-1"><b>Ordini</b></b-navbar-brand>
                </b-navbar-nav>
            </b-navbar>
          </div>

          <!-- Nav F -->
 

        <!-- Table S  -->
<div class="scrollBar">
    <b-table striped hover :items="employees" :fields="fields">
        <template v-slot:cell()="{ value, item, field: { key }}">
        <template v-if="!item.isEditing">{{ value }}</template>
        <b-form-input v-else v-model="item[key]" />
        </template>

        <template v-slot:cell(actions)="{ item }">
            <b-dropdown variant="primary" text="Change">
            <b-dropdown-item @click="onEdit(item)">{{ item.isEditing ? 'Save' : 'Edit' }}</b-dropdown-item>
            <b-dropdown-divider></b-dropdown-divider>
            <b-dropdown-item>Delete</b-dropdown-item>
            </b-dropdown>
        </template>
    </b-table>
</div>
<!-- Table F  -->

          <!-- Order S -->
          <div class="navTop">
            <b-navbar type="dark" variant="dark">
                <b-navbar-nav>
                </b-navbar-nav>
            </b-navbar>
          </div>
          <!-- Order F -->


          <!-- Send S -->
          <div>
               <button type="button" class="block"><b>Invia</b></button>
         </div>
          <!-- Send F -->

      </div>
    </div>
</template>

<script>
// 
  export default {
    data() {
      return {
          employees: [
              {
          id: 0,
          Name: "Jane",
          Quantitiy: 3,
          Price: 12
        },
        {
          id: 1,
          Name: "Peter",
          Quantitiy: 2,
          Price: 12
        },
        {
          id: 2,
          Name: "Peter",
          Quantitiy: 1,
          Price: 12
        },
        {
          id: 3,
          Name: "Peter",
          Quantitiy: 2,
          Price: 12
        },
        {
          id: 4,
          Name: "Peter",
          Quantitiy: 2,
          Price: 12
        },
        {
          id: 5,
          Name: "Peter",
          Quantitiy: 2,
          Price: 12
        },
        {
          id: 6,
          Name: "Peter",
          Quantitiy: 2,
          Price: 12
        }
      ],
      fields: [{
          key: 'Name',
        },
        {
          key: 'Quantitiy',
        },
        {
          key: 'Price',
        },
        {
          key: 'actions',
          label: 'Change'
        }
      ]
      }
    
    },
      computed:{
    rows(){
      return this.employees.length
    }
  },
    methods:{
        onEdit(item) {
      if (item.isEditing)
        item.isEditing = false;
      else
        this.$set(item, 'isEditing', true)
    }
  }
  }
</script>

<style scoped>
.block {
  display: block;
  width: 100%;
  border: none;
  background-color: #0275d8;
  color: white;
  padding: 14px 28px;
  font-size: 16px;
  cursor: pointer;
  text-align: center;
}

.scrollBar{
  max-height: 300px;
  margin-bottom: 10px;
  overflow:scroll;
  -webkit-overflow-scrolling: touch;
} 
.cardSet{
    display: inline-block;
    margin: 0;
}

.ulClass{
    margin-top: 20px;
}
 
.orderText{
    text-align: center;
}

@media screen and (max-width: 780px) {
  div.scroll{
  margin:1px, 1px;
  padding:1px;
  width: 300px;
  height: 680px;
  overflow-x: hidden;
  overflow-y: auto;
  text-align:justify;
  }
}

@media screen and (max-width: 480px) {
  div.scroll{
  margin:1px, 1px;
  padding:1px;
  width: 200px;
  height: 680px;
  overflow-x: hidden;
  overflow-y: auto;
  text-align:justify;
  }
}

.itemDisplay{
    display: inline;
    padding: 3px;
    margin-right: 30px;

}

.delBtn{
    margin-left: 30px;
    margin-top: 5px;
}
</style>
