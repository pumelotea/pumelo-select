<template>
  <div id="app" style="height:100vh">
     <section class="panel panel-default" style="padding:40px;height:100vh">
      <div class="form-group" style="padding:30px">
        <label class="col-sm-2 control-label">值{{selectedVal}}-{{searchKey}}</label>
        <div class="col-sm-10">
          <select-x :data="list" v-model="selectedVal" @on-search="searchCallback" @change="onChange" class="col-md-6"></select-x>
        </div>
      </div>
      <div class="form-group" style="padding:30px">
        <label class="col-sm-2 control-label">值{{selectedVal1}}</label>
        <div class="col-sm-10">
            <group-select-x :data="list1" v-model="selectedVal1" class="col-md-6"></group-select-x>
        </div>
      </div>
      <div class="form-group" style="padding:30px">
        <label class="col-sm-2 control-label">值{{selectedVal1}}</label>
        <div class="col-sm-10">
            <group-select-x :data="list1" v-model="selectedVal1" class="col-md-6" :disabled="true"></group-select-x>
        </div>
      </div>
     </section>
  </div>
</template>

<script>
import SelectX from '@/components/Select'
import GroupSelectX from '@/components/GroupSelect'
export default {
  name: 'App',
  data(){
    return{
      list:[{value:'1',text:"South Carolina"},{value:'2',text:"Vermont"},{value:'3',text:"Virginia"},{value:'4',text:"West Virginia"}],
      list1:[{group:'aaaa',data:[{value:'1',text:"South Carolina"}]},{group:'bbbb',data:[{value:'2',text:"Vermont"}]},{group:'fasdas',data:[{value:'3',text:"Virginia"}]},{group:'zxczxc',data:[{value:'4',text:"West Virginia"}]}],
      selectedVal:'2',
      selectedVal1:'1',
      searchKey:''
    }
  },
  components: {
    SelectX,GroupSelectX
  },
  methods:{
    searchCallback:function(data){
      console.log(data)
      this.searchKey=data
    },
    onChange:function (data) {
      console.log(data)
    }
  }
}
</script>
