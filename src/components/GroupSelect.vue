<template>
  <div>
    <div style="position: relative;">
      <a @click="toggle"><input v-model="text" type="text" class="form-control input-sm " :class="!disabled?'bg-white':''"  style="cursor: pointer;padding: 8px" :disabled="disabled" readonly/></a>
      <div v-show="isShow" class="drop-list-container">
        <div class="drop-search"><input class="form-control drop-search input-sm" type="text" @keyup.enter="search" v-model="searchKey"/></div>
        <ul class="drop-list">
          <template v-for="groupItem,i in list">
            <li class="drop-group">{{groupItem.group}}</li>
            <li class="drop-item" v-for="item,j in groupItem.data" :value="item.value" @click="choose(i,j)">{{item.text}}</li>
          </template>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    props:{
      data:{
        type:Array,
        required: true
      },
      value: {
        required:false
      },
      disabled: {
        type:Boolean,
        required:false,
        default:false
      }
    },
    data(){
      return{
        isShow:false,
        val:this.value,
        text:'',
        list:this.data,
        searchKey:''
      }
    },
    methods:{
      show:function () {
        if(this.disabled===false)
          this.isShow = true
      },
      hide:function () {
        this.isShow = false
      },
      toggle:function () {
        if(this.disabled===false)
          this.isShow = !this.isShow
      },
      choose:function (i,j) {
        this.val = this.list[i].data[j].value
        this.text = this.list[i].data[j].text
        this.hide()
        this.$emit('change', {value:this.val,text:this.text})
      },
      set:function (val) {
        for(let group of this.list){
          for(let item of  group.data){
            if(item.value === val){
              this.val = val
              this.text = item.text
            }
          }
        }
      },
      search:function () {
        this.$emit('on-search', this.searchKey)
      },
      handleDocumentClick(e) {
        if (!this.$el.contains(e.target)) {
          this.isShow = false;
        }
      }
    },
    watch:{
      val(val){
        this.$emit('input', val);
      },
      value(val){
        this.val = val
        this.set(val)
      },
      data(val){
        this.list = val
      }
    },
    mounted(){
      this.set(this.value)
      document.addEventListener('click', this.handleDocumentClick);
      document.addEventListener('touchstart', this.handleDocumentClick);
    }
  }
</script>
<style>
  .drop .active {
    border-bottom: none;
    border-bottom-left-radius: 0px;
    border-bottom-right-radius: 0px;
  }
  .drop-group{
    padding-left:5px;
    padding-right:5px;
    font-weight: bold;
    font-size: 13px;
  }
  .drop-search {
    padding: 10px;
    border-left: 1px solid #cbd5dd;
    border-right: 1px solid #cbd5dd;
  }
  .drop-list-container{
    background: #ffffff;
    border-bottom-left-radius: 2px;
    border-bottom-right-radius: 2px;
    z-index: 2000;
    position: absolute;
    width: 100%;
  }

  .drop-list{
    background: #ffffff;
    list-style-type:none;
    padding:5px;
    border-bottom: 1px solid #cbd5dd;
    border-left: 1px solid #cbd5dd;
    border-right: 1px solid #cbd5dd;
    border-bottom-left-radius: 2px;
    border-bottom-right-radius: 2px;
    width: 100%;
    max-height: 300px;
    overflow: auto;
    margin-bottom: 0px;
  }
  .drop-item {
    padding: 3px 15px;
    font-size: 10px;
  }

  .drop-item:hover{
    background: #848484;
    color: #fff;
    cursor: pointer;
  }
</style>
